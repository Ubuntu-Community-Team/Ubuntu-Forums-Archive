---
title: "Mounting another linux partition"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-09
On my slave drive I have a linux partition, and two ntfs partitions that I want to mount.  I have successfully mounted the two windows partitions in fstab,  I use

mount /dev/hdb4 /mnt/L

to mount the linux partition, but I don't know the equivalent entry into fstab to do this.   Thanks.

---

### Post by Kyral on 2005-11-09
/dev/hdb4 /mnt/L (ext2/ext3/ReiserFS) defaults,users,rw 0 0

Replace (ext2/ext3/ReiserFS) with whatever they are formatted in

---

### Post by Todd_Z on 2005-11-09
I have no idea what fs they are :-\ n00bisms

---

### Post by Kyral on 2005-11-09
you could try putting auto there ;P

---

### Post by Todd_Z on 2005-11-12
I tried auto, and it worked perfectly - and during boot i saw that it said "you didn't specify what type of partition that is, so i'll try reiserfs" and that worked, so i set it to reiserfs and its allll good.  Thanks for the help.

---

