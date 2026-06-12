---
title: "what version of ubuntu am i running?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by rcmayfld on 2007-04-24
output of /proc/version
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5 -8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005

I installed from Ububtu 6.06 disk, then
apt-get update, then
apt-get upgrade, then
apt-get dist-upgrade

is this dapper ? feisty fawn ? 
need correct repos for non-free

thanx 
rick

---

### Post by clevin on 2007-04-24
check your /etc/lsb-release file's content, it should tell you about the version of the ubuntu u are running.

---

### Post by silverglade00 on 2007-04-24
Cool! That's much better than cat /etc/issue. Thanks!

---

### Post by Bachstelze on 2007-04-24
2.6.10 ?? That's Hoary, man, are you sure you didn't use the wrong CD ?

---

### Post by rcmayfld on 2007-04-24
this is my version=.......
how do i update, broadband to the latest version?
rick

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=5.04
DISTRIB_CODENAME=hoary
DISTRIB_DESCRIPTION="Ubuntu (The Hoary Hedgehog Release)"
rick@tc211-scene:~$ cat /etc/issue
Ubuntu 5.04 "Hoary Hedgehog" \n \l

---

### Post by Bachstelze on 2007-04-24
Upgrading will be a pain, better do a fresh install.

---

### Post by StarscreamD on 2007-04-24
```
sudo apt-get dist-upgrade
```
Update your /etc/apt/sources.list to change the Hoary to Feisty. After a restart, that should do it!

---

### Post by Bachstelze on 2007-04-24
That is roughly equivalent to a reinstall, because that will break his system quite badly...

---

### Post by rcmayfld on 2007-04-24
thanx for the information
i'll reinstall .....
rick

---

### Post by Bachstelze on 2007-04-24
If you want to try to upgrade, you'll need to upgrade your Hoary to Breezey, then Breezy to Dapper, then Dapper to Edgy, then Edgy to Feisty. You can try that if you want but it seems too much hassle to me so if I were you, I'd go with a reinstall.

---

