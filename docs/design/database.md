## テーブル設計
- users
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
| id| int | |PRIMARY||YES|
| name |  varchar(100)| ||||
| email |  varchar(25)| |UNIQUE|||
| password |  varchar(20)| ||||

- requests
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
| id| int | |PRIMARY||YES|
| user_id |int| |FOREIGN|||
| creator_id |int| |FOREIGN　→ users.id|||
| title |varchar(200)|||||
| body |text|||||
| current_amount|bigint(10)|||||
| start_date |datetime|||||
| end_date |datetime|||||
| lowest_amount |int|||||
| target_amount |int|||||
|status|enum| ||||
Rails側でJSTに変換

- messages
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
| id| bigint | |PRIMARY||YES|
| reciver_id| int| |FOREIGN　→ users.id|||
| title |varchar(200)|||||
| body| text | ||||
| message_id|int| ||||
|status|enum| ||||

- notifications
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id|bigint| |PRIMARY||YES|
|user_id|int| |FOREIGN|||
|message_id|int| |FOREIGN|||
|read_at|datetime|||||

- reviews
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
| id | bigint | |PRIMARY||YES|
| reviewer_id |int| |FOREIGN → users.id, UNIQUE(uk_reviewer_request)|||
| creator_id |int| |FOREIGN → users.id|||
| request_id |int||FOREIGN, UNIQUE(uk_reviewer_request)|||
| rating |int|||||
| comment|text| ||||

- supporters
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id|bigint| |PRIMARY||YES|
|supporter_id|int| |FOREIGN → users.id|||
|request_id|int| |FOREIGN|||
|amount|int| ||||

- request_tags
  
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id| int | |PRIMARY||YES|
|tag_id| int| |FOREIGN, UNIQUE(uk_tag_request)|||
|request_id| int| |FOREIGN, UNIQUE(uk_tag_request)|||

- creator_tags
| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id| bigint | |PRIMARY||YES|
| creator_id |bigint| |FOREIGN, UNIQUE(uk_tag_creator)|||
| tag_id |bigint| |FOREIGN, UNIQUE(uk_tag_creator)|||
| score |int| ||||

- portfolios

| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id| int | |PRIMARY||YES|
| creator_id |int| |FOREIGN → users.id|||
| title |varchar(200)|||||
| body| text | ||||

- blocks

| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id| bigint | |PRIMARY||YES|
| blocker_id |int| |FOREIGN → users.id|||
| blocked_id |int|||||

- tags

| カラム名 | データ型 |NULL |キー|初期値|AUTO INCREMENT|
|-|-|-|-|-|-|
|id| bigint | |PRIMARY||YES|
| name|varchar(15)| ||||

