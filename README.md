# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


# テーブル設計

## users テーブル

|  Column  |  Type  |   Options   |
| -------- |  ----  | ----------- |
|   name   | string | null: false |
|  email   | string | null: false |
| password | string | null: false |

### Associatiion

- has_many :room_users
- has_many :room, through: room_users
- has_many :messages

## rooms テーブル

|  Column  |  Type  |   Options   |
| -------- |  ----  | ----------- |
|   name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

|  Column  |    Type    |          Options           |
| -------- |  --------  | -------------------------- |
|   user   | references | null: false, foreign: true |

### Associations

- belongs_to :room
- belongs_to :user

## messages テーブル

|  Column  |    Type    |          Options           |
| -------- |  --------  | -------------------------- |
|  content |   string   |                            |
|   user   | references | null: false, foreign: true |
|   room   | references | null: false, foreign: true |

#### Associations

- belongs_to :room
- belongs_to :user
