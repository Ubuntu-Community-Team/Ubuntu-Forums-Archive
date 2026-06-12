---
title: "partition hd make space for Breezy badger 5.10"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-11-25
Hello,

I am about to do a dual boot with XP

how to partirion 16.gb FAT32 partition

IE
how to 
make mount point
ext2
swap.

which application is most suitable.
raid, resizer
lvm?

thanks

:smile:

---

### Post by suRoot on 2005-11-25
Are you trying to save any data on the drive?  Do you currently have XP on the drive & want to resize it so you can install Breezy, or do you want to just wipe the drive clean & install both OS'es?

---

### Post by xstation on 2005-11-25
Thanks for your post.


It is all free space 
on C drive xp
on d drive 16gigs for brezzy currently formated in fat32

The 16 gigs is for root, data and swap


thanks

xstation:smile: :smile:

---

### Post by suRoot on 2005-11-25
See this:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

and this:

[http://ubuntuforums.org/showthread.php?t=94212&highlight=dual+boot+partition]("http://ubuntuforums.org/showthread.php?t=94212&highlight=dual+boot+partition")

Both of which should get you up & running.

Good luck.

---

### Post by xstation on 2005-11-25
Thanks for your post.

The  links were pretty strightforward.

I am sending this post from the local internet shop.????

I have a hard drive looks like this

1 primary 2.1 gb hda1
2 primary 21.0gb hda2 (xp)
3 primary 16.9 gb had 3

all are fat32

I changed as follows

1 PRIMARY 2,1 GB HDA1
2 PRIMARY 21.0 GB HDA2
3 PRIMARY 2.O GB swap hda3
4 PRIMARY 14.9 HDA4

isntall ran almost right away I did not seem to know what was happing.

Install base system error

the debootstrap programme exited with an error(return value 1)
check /target/ver/log/bootstrap.log for details

I restarted windows it did start went back into unbuntu to get 
hard drive details came out BUT when going back into
windows a second time
invaid partition --cannot run setup.

so I went back into ubuntu and changed everything back as it was
1 primary 2.1 gb hda1
2 primary 21.0gb hda2 (xp)
3 primary 16.9 gb had 3



but still get the invaild partition error.

xstation:(

---

### Post by Schmots on 2005-11-25
This is actually a point where Windows is being cranky.  Whats on your 2.1 gig partition?  Why is it there.  To get linux to duel boot with windows and still have windows happy its been my experiance that you need to put windows on your first partition of your first drive.

---

### Post by xstation on 2005-11-25
It came with laptop is information about the acer  travelmate labtop apprently it is need needed when you do a system recovery.


xstation:p

---

