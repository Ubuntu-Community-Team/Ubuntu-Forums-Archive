---
title: "apt-get"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Manoau2002 on 2006-05-13
I was wondering how to use apt-get to update my system. I have read on several different webpages on how to do it but I always get the following message:

manoau2002@TheMan:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
manoau2002@TheMan:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
manoau2002@TheMan:~$

I was wondering if anyone could shed some light on this.

---

### Post by sailor2001 on 2006-05-13
you have to use sudo first . sudo apt-get update

---

