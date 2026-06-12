---
title: "what is the latest sources.list file?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-28
where can I find the latest info on the sources.list file?  I wanted to update the list because i get some errors when I try to install "linux-image-2.6.12-10-386"

Can someone help?

---

### Post by Dr. Nick on 2005-12-28
run sudo apt-get update. The file  only changees on a new ubuntu release

---

### Post by Nimefurahi on 2005-12-28
If your /etc/apt/sources.list includes:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
#
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
#
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
#
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
#
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#

and run "sudo apt-get update" as Dr. Nick suggested, you should have no problems with sudo apt-get -s install linux-image-2.6.12-10-386

---

### Post by jimrz on 2005-12-28
try [**[COLOR="Sienna"]this[/COLOR]**]("http://psychocats.net/linux/sources.php") been working well for me

---

