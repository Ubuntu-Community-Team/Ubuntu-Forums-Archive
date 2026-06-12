---
title: "3rd party software- another newb needs help"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by tommystoy on 2007-01-28
Another newb question.

I downloaded a linux version of a 3rd party software package that I have been using on XP.

I extracted all of the files from the .tgz file into a new  folder on a mounted external usb drive. This folder contains several html help files, a data file (.dat) and the executable.   

How do I run the executable? Double clicking the executable's icon does nothing.
I tried to create a launcher but couldn't get it to work.

TIA,
Tom:confused:

---

### Post by taurus on 2007-01-28
What app are you talking about and what is the output of this command from where you have unpacked it?

```
ls -la
```

---

### Post by tommystoy on 2007-01-29
The app is called Vuescan.

tommy@tommy-ubuntu:~/Vuescan$ ls -la
total 6160
drwx------  3 tommy tommy    4096 2007-01-28 13:42 .
drwxr-xr-x 27 tommy tommy    4096 2007-01-29 23:26 ..
drwx------  2 tommy tommy    4096 2007-01-28 13:42 html
-rwx------  1 tommy tommy     498 2005-05-01 05:53 purchase.htm
-rwx------  1 tommy tommy     529 2004-05-07 04:04 upgrade.htm
-rwx------  1 tommy tommy 4659900 2006-12-30 09:58 vuescan
-rwx------  1 tommy tommy  288054 2004-04-08 14:20 vuescan.bmp
-rwx------  1 tommy tommy 1236721 2006-11-23 14:09 vuescan.dat
-rwx------  1 tommy tommy   72189 2006-12-28 10:56 vuescan.htm

---

### Post by taurus on 2007-01-29
Try

```
./vuescan
```

---

