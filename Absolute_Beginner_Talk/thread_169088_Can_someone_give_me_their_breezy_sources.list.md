---
title: "Can someone give me their breezy sources.list?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-01
Can someone post their sources.list (**_breezy only_**)? And it's got to be a perfect one, not a corrupt one like mine, please.:(
You can find it in /etc/apt

---

### Post by jasay on 2006-05-01
I'm on Dapper and don't have a copy of my old breezy sources.list, but I've enver had an issue with one generated from [here]("http://www.ubuntulinux.nl/source-o-matic").  You might even find some new repos you didn't know about.:)

---

### Post by user1397 on 2006-05-01
Forgot to mention that I wanted an original list, only with the repos that come off of a fresh breezy install. Thanks in advance.

---

### Post by manicka on 2006-05-01
aysiu also has some reliable sources lists here

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by user1397 on 2006-05-01
If this is all I got, is it correct:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

---

### Post by linear on 2006-05-02
It looks OK, but it's not what you would get with a fresh Breezy install. I don't think universe/multiverse or anything from breezy-backports are enabled by default.

---

### Post by user1397 on 2006-05-02
Thanks for all the replies guys, they helped

---

