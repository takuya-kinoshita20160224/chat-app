＃テーブル設計

## users テーブル

｜ Column   | Type   | Option      |
｜--------  | ------ | ------------|
| name     | string | null: false |
| email    | atring | null: false |
| password | string | null: false |

### Association
- has_many :room_users
- has_many :rooms, through: room_users
- has_many : messages

## rooms テーブル

｜ Column   | Type   | Option      |
| --------- | ------ | ----------- |
| name      | string | null: false |

### Association
- has_many :room_users
- has_many :users, through: room_users
- has_many : messages

## room_users テーブル

| Column    | Type   | Option                           |
| --------- | ------ | -------------------------------- |
| user_id   | references | null: false. foreign_key: true |
| room_id   | references | null: false. foreign_key: true |

### Association
- belongs_to :room
- belongs_to :user

## messages テーブル

| Column    | Type   | Option                           |
| --------- | ------ | ---------------------------------|
| content      | string   |
| user_id   | references  | null: false, foreign_key: true |
| room_id   | references  | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :room