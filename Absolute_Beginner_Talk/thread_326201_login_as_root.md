---
title: "login as root"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by JParkus on 2006-12-27
im trying to reinstall alsa so i can get sound its giving this message

parkus@parkus:~$ apt-get install libasound2 alsa-utils alsa-oss
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

how do i switch to root or sudo?

---

### Post by tzulberti on 2006-12-27
You could use "sudo su" to get as root, or you could do "sudo apt-get install XXX".... The second one is more secure...

---

### Post by Regel on 2006-12-27
sudo apt-get install ...

sudo makes you a root for a while.

---

### Post by JParkus on 2006-12-27
that worked but i now have the following message

parkus@parkus:~$ sudo apt-get install libasound2 alsa-utils alsa-oss
Reading package lists... Done
Building dependency tree... Done
libasound2 is already the newest version.
alsa-utils is already the newest version.
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate

if i have the newest version why dont i have sound

---

