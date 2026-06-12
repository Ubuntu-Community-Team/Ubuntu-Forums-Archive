---
title: "Repositries"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-01
Hi, I'd like to add something to repositries. I suppose that when I type this line.
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

> sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

Text editor will run and I can add things but nothing happenes.
I wonder why.

PS,
What I like to do is Add these two lines to repositries.

> deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper/
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper-ja/ 

---

### Post by Perfect Storm on 2006-10-01
did you run
```
sudo apt-get update
``` 
afterwards?

---

### Post by i-m-p on 2006-10-01
Thanks!

Perfecto!:KS

---

