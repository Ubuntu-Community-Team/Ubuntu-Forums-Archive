---
title: "/home folder and file system question"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-12-29
I am now beginning to see the folly in not putting /home on its own partition.  I am already dreading the pain that will ensue when I go to Dapper.  So my question is this:
Can I move /home?  I just got a new drive for xmas that I'd like to make good use of, can I just move /home over there?  -pete

---

### Post by psusi on 2005-12-29
Yes, if you mount the new drive in /mnt you can mv /home /mnt then remount the drive in /home instead of /mnt.  

You will want to do this in single user mode though.  Either choose the rescue option from the grub boot menu or run sudo init 1.

---

### Post by jrib on 2005-12-29
I followed [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866) a few weeks ago and it worked great

---

### Post by TeeAhr1 on 2005-12-29
Thx, y'all!

---

