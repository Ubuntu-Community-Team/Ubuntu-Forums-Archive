---
title: "Format a USB Jump Drive ..."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-29
How do you format a USB Jump Drive?  I tried Gparted but it core dumps.

Isn't there some commands to make a partition and then format it FAT32?

Carl

---

### Post by natman on 2007-11-29
try this, frist umount the ub drive
[HTML]sudo fdisk -l
[/HTML]
Check via the file size but the usb should be sdb
> fdisk /dev/sdb*
d
if there is only one partition ok, but if there is more type a number of partition to delte after. I cant remember all the commands but if you ask for help while in fdisk it will show all the options, or > man fdisk
When your finished type "w" to write the changes to the disk.

---

### Post by bodhi.zazen on 2007-11-29
I wrote a script to do this :

[http://ubuntuforums.org/showthread.php?t=302724](http://ubuntuforums.org/showthread.php?t=302724)

---

### Post by Gingerman on 2008-06-06
Thank you for doing this work.

I noticed your tag line quote from the Tao of Ubuntu.
Check out my most recent post in the beginners' forum.  Your philosophy hasn't been my experience in here.  Maybe I'm slow, but my experience is not good so far.

---

### Post by bodhi.zazen on 2008-06-06
> **Gingerman said:**
> Thank you for doing this work.

I noticed your tag line quote from the Tao of Ubuntu.
Check out my most recent post in the beginners' forum.  Your philosophy hasn't been my experience in here.  Maybe I'm slow, but my experience is not good so far.

link ?

---

