---
title: "problem installing timidity"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-22
I want to install the program timidity so that I can play .mid files. Every time I try to install it, ubuntu won't let me. I would greatly appreciate any help you can give. I have posted my output here. I was logged in as root and did su but it still wouldn't let me install timidity. 


jprblinux@jprblinux-desktop:~$ apt-get install timidity
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Thanks


:popcorn:

---

### Post by zombiepkx on 2007-02-22
Put sudo in front of that.

example

sudo apt-get install roflcopters

You'll be prompted for your password then :)

---

