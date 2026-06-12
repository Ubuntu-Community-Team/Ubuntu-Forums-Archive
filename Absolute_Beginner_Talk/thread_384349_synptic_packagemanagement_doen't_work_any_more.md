---
title: "synptic packagemanagement doen't work any more"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by desiretosee on 2007-03-14
after I installed textlive full,
the synptic packagemanagement works not properly any more.
always show the message:
error processing texlive-lang-german (--configure):
 subprocess post-installation script returned error exit status 1

not only german, all the other languages will show this message

with sudo apt-get install -f can not help either.
I need help really badly. 
three day Ubuntu user.

---

### Post by benfindlay on 2007-03-14
try typing ```
sudo dpkg --configure -a
``` into a terminal window.

---

### Post by desiretosee on 2007-03-14
Thank you very much. But It didn't work. :confused:

---

### Post by familyjules74123 on 2007-03-14
worst case senario: fresh install of your ubuntu release.

what version are you using? dapper, edgy, etc?

---

### Post by DaveyG on 2007-03-14
Had the same problem with synptic manager the other day....  got rather angry then decided to do a fresh re-install :(

---

### Post by desiretosee on 2007-03-15
my version is Ubuntu 6.10 Edgy. please! I dont have cd or dvd rom, I dont want to reinstall anymore. is there better way to resolve this. I was seduced by linux, because they say, it is stable and never need to reinstall. not like windows

---

