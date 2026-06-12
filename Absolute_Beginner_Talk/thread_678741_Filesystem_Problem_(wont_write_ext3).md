---
title: "Filesystem Problem (wont write ext3)"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by thebazman on 2008-01-26
hi
i can use the live cd of any distro but when i try to install it. it crashes at 5% when formating partion with ext3 this is with any distro apart from elivegem and elive stable.
helps  appreciated

thanks in advance

---

### Post by PmDematagoda on 2008-01-26
Did you try and install Linux using a file system other than ext3 such as JFS or ReiserFS?

---

### Post by thebazman on 2008-01-26
ive tried reiserfs that failed at 41% yet my installed system is elive and that uses reiserfs and installs no problem 

i did try install elive with ext3 but it also crashed .

---

### Post by articpenguin on 2008-01-30
how big is your harddisk?

here is my experience with filesystems on my 500gig harddisk
ext3= slow, fsck is 50 mins with 128k files with 5% space used
xfs=works good but corrupted on a hard power off
jfs= very fast, current fs i am using right now on it. 

reiserfs is a joke.

---

