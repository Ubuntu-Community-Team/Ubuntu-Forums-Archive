---
title: "Changing permissions of `/media/sda1': Read-only file system"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by derekho55 on 2006-08-09
Right now I can only mount my usb hard drive through the plug and play ( not through /etc/fstab) and so far i can only read the files inside, and cannot write. 

So I tried chmod-ing the drive, but it fails, saying it is a "read-only file system".

I have tried to play with my fstab and got stuck with the file system type. So I tried to use "sudo parted /media/sda1 print" to find out my filesystem type, but it outputs as follows:

Warning: Unable to open /media/sda1 read-write (Is a directory).  /media/sda1
has been opened read-only.
Warning: Unable to open /media/sda1 read-write (Is a directory).  /media/sda1
has been opened read-only.
Error: Unable to open /media/sda1 - unrecognised disk label.

What do you guys suggest?

---

### Post by derekho55 on 2006-08-09
Sorry but I have forgot to post up my specs:

Dapper (Kubuntu 6.06)
Running on Sony VAIO VGN -B100B

---

