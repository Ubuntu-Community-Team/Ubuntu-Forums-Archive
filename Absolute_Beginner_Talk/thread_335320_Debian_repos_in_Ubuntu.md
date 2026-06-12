---
title: "Debian repos in Ubuntu"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by pcomelade on 2007-01-10
Hi all,

Is it possible (and recommendable) to include Debian specific repos to the Ubuntu's source.list? Ubuntu only offer an old version of a program that I need (hmmer) and I've seen in "apt-get.org" that these Debian repos has the latest version of the program:

[http://biolinux.df.ibilce.unesp.br/pacotes/deb](http://biolinux.df.ibilce.unesp.br/pacotes/deb) ./
[http://www.biodec.com/opensource/debian](http://www.biodec.com/opensource/debian) sarge main

Thanks in advance!

M;

---

### Post by jvc26 on 2007-01-10
It is definitely possible to do, I'm not sure about recommendable, as it may cause you problems with updating to very new and unstable releases? (I may be wrong here, but you could possibly end up replacing some of your existing Ubuntu apps with more upgraded versions which are still in testing?) You definitely can use them to get the app in question, so you could try: put the repo in, sudo apt-get update then install the app, then remove the repo from your list (or simply comment it out) and sudo apt-get update again so that your updater doesnt detect newer versions which arent completely tested yet. I'm not honestly sure tho :)
Il

---

### Post by pcomelade on 2007-01-10
That's what I thought to do. Only add the repo to upgrade this program and comment it after that.

Thanks a lot!

M;

---

### Post by kerry_s on 2007-01-10
I would say stick with ubuntu repos. If just must have newer grab it from "edgy" or "feisty", feisty would be the most up to date or latest. All you have to do is change the name in your /etc/apt/sources.list.

sudo gedit /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse universe 

to

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe 

or

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

---

### Post by pcomelade on 2007-01-10
Just to say that I've already included the debian "repo" in the source.list and updated the package. Everything seems Ok, no complains!

Thanks for the help!

M;

---

