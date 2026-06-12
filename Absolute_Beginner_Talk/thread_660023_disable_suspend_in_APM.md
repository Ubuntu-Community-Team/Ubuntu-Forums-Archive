---
title: "disable suspend in APM"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2008-01-06
I recently installed APMD on my laptop, so i could keep track of how much battery i had left (from console).
However, after doing so, it suspends my computer as soon as it has been idle for 5 minutes (i think it is 5 minutes) on battery power.
Is there a way i can configure when it should do what (from console, i have no GUI) or maybe completely disable suspend?

---

### Post by blueridgedog on 2008-01-08
Start with man apmd

Then look around in the directory structure under /etc/apm.  Perhaps there is a script in the event.d directory that is being triggered.

root@ripstop:/etc/apm# pwd
/etc/apm
root@ripstop:/etc/apm# ll
total 40
drwxr-xr-x   7 root root  4096 2007-10-15 19:28 .
drwxr-xr-x 132 root root 12288 2008-01-07 22:48 ..
-rwxr-xr-x   1 root root  3849 2007-05-23 08:59 apmd_proxy
drwxr-xr-x   2 root root  4096 2007-10-15 19:28 event.d
drwxr-xr-x   2 root root  4096 2007-05-23 08:59 other.d
drwxr-xr-x   2 root root  4096 2007-10-15 19:28 resume.d
drwxr-xr-x   2 root root  4096 2007-10-15 19:28 scripts.d
drwxr-xr-x   2 root root  4096 2007-10-15 19:28 suspend.d

---

