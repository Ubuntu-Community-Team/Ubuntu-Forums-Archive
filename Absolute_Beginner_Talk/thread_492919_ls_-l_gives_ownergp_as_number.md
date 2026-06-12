---
title: "ls -l gives owner/gp as number"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by merkel on 2007-07-05
Maybe this is normal, but I don't know what it means.  Can someone help?  I unzipped and untarred a package into a directory.  Now when I run 'ls -l' I get the output below.  Why are there numbers for owner and group, instead of names like root root?  Does that mean something?  When I try to run a patch as sudo, I get a 'permission denied' error.

$ ls -l SNNSv4.2
total 236
-rw-r--r-- 1 root root  3035 2007-07-04 19:50 config.h
drwxr-xr-x 2 4322 1004   304 1998-09-03 09:41 configuration
-rwxr-xr-- 1 4322 1004 84830 1998-09-03 09:44 configure
-rw-r--r-- 1 4322 1004  1236 1994-10-06 07:56 default.cfg
drwxr-xr-x 2 4322 1004    48 1998-09-03 09:41 ENZO
drwxr-xr-x 2 4322 1004  4520 1998-09-03 09:53 examples
-rw-r--r-- 1 4322 1004 82224 1998-03-05 08:57 help.hdoc

---

### Post by jasonlfunk on 2007-07-05
My guess is whoever made the original file somehow retained ownership of the files, or perhaps when you extracted it you told it to retain ownership. Anyways, all files store the owner and group as numbers. You're shell intreperts the numbers into names. Your system doesn't have any users that match those numbers therefore they remain numbers.

---

### Post by merkel on 2007-07-05
That makes sense.   I extracted using:

sudo tar -oxf SNNSv4.2.tar

and the owner is now root.  the '-o' with tar was what i needed.

Thanks!

---

