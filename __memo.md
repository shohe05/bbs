### APIリスト
- スレッド作成API
- 投稿API
- スレッド内容取得API

### ユビキタス言語

- スレッド（Thread）
    - 掲示板のスレッド。以下の属性を持つ
        - スレッドID
        - スレッド名
        - 投稿リスト
- スレッドID（ThreadId）
    - 掲示板を一意に識別するID
- スレッド名（ThreadName）
    - スレッドの名称
- 投稿（Post）
    - 投稿。スレッドに対して行う。以下の属性を持つ
        - スレッドID: 紐づくスレッドのスレッドID
        - 本文
        - 投稿日時
- 本文（PostBody）
    - 投稿の内容
- 投稿日時
    - 投稿を行った日時


### クラス設計

```
Acme
    BBS
        Application
            Controllers
                ThreadController.php
                PostController.php
            Requests
                CreateThreadRequest.php
                CreatePostRequest.php
            UseCases
                CreateThread.php
                CreatePost.php
                GetThread.php
        Domain
            Models
                Domainable.php (I)
                Thread
                    Thread.php
                    ThreadId.php
                    ThreadRepositoryInterface.php (I)
                Post
                    Post.php
                    PostBody.php
                    PostRepositoryInterface.php (I)
            Exceptions
        Infrastructure
            Eloquents
                AppEloquent.php
                EloquentThread.php (Imp: Domainable)
                EloquentPost.php (Imp: Domainable)
            Repositories
                Eloquent
                    EloquentThreadRepository.php (Imp: ThreadRepositoryInterface)
                    EloquentPostRepository.php (Imp: PostRepositoryInterface)
```
