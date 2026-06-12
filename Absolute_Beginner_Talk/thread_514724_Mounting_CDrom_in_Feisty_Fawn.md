---
title: "Mounting CDrom in Feisty Fawn"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by rosco99 on 2007-08-01
I have just installed ubuntu FF 7.04. How do I mount the CDrom? I right click on the icon and say mount and I get an error-"-Cannot mount the device. May not be a disk in the CDrom." I put a disk in and still get same error. I had kubuntu 6.01 installed and the CDrom is mounted automatically(on the same computer)

---

### Post by Benbow on 2007-08-01
Not wishing to hijack your post but I am currently trying suse 10.2 and unfortunately finding it difficult and one of the problems is exactly the same as yours. Lets hope that someone comes up with an answer.

---

### Post by tomcheng76 on 2007-08-01
plz add a line like this into /etc/fstab
> 
/dev/sdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

where "sdd" is your CDrom drive,  u need to change it your self
Also
> 
sudo mkdir /media/cdrom0
sudo ln -s /media/cdrom0 /media/cdrom

if you cant find cdrom and cdrom0 is your /media folder

then you can simply 
> 
sudo mount /dev/sdd

to mount the cdrom

and sudo umount /dev/sdd to umount it

---

