# Vagrant + VirtualBox

## ネットワーク周りの設定
### vagrant sshじゃなくてホストからIP宛にssh接続する
- ping ipできるように
- ssh vagrant@ipできるように

https://www.wakuwakubank.com/posts/481-tool-vagrant-private-network/
https://qiita.com/ftakao2007/items/b332f562b0ea74e9f97e

## docker
### vagrant内で立ち上げたコンテナをローカル（ホスト）のブラウザで表示する
- localhostにブラウザで表示するアプリ用のポートを転送した上でSSH
`ssh -g -L 8080:localhost:8080 vagrant@192.168.33.10`
- vagrant内でdocker run
`sudo docker run --name nginx00 -d -p 8080:80 nginx:latest`
- ローカルのブラウザで以下にアクセス
`http://localhost:8080`

### ポート転送を行わない場合
- 普通にsshアクセス
`ssh vagrant@192.168.33.10`
- vagrant内でdocker run
`sudo docker run --name nginx00 -d -p 8080:80 nginx:latest`
- ローカルのブラウザで以下にアクセス
`http://192.168.33.10:8080`
