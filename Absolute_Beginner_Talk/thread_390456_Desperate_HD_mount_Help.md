---
title: "Desperate HD mount Help"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-03-22
Hi folks 

Sorry to post again ,,but this is the same a s the blue screen of death ,,, When I use my USBs on the laptop  ( ubuntu 6.06 lts )  and transfer back to the desktop , the Desktop  changes the permissions 

When I try to open them,   it says you must be root to open them 

here is the output of fsab 

s@s-desktop:~$ sudo fdisk -l
Password:
\
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1284    10313698+   7  HPFS/NTFS
/dev/hda2            1285        9729    67834462+  83  Linux

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4870    39118243+   c  W95 FAT32 (LBA)
s@s-desktop:~$ \sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
s@s-desktop:~$ \sudo mount /dev/sda1
mount: mount point /media/sda1 does not exist
s@s-desktop:~$

Its the 40 gig drive I am concerned about ..

How can I swap between computers with out fluffing around ....

At the moment this is SUPER critical as my customers files are on that drive and I NEED to use the desktop to modify them 


PLEASE ( underlined ..chocolates attached ,,, money pinned to it )  help 

Kind regards Stephen

---

### Post by alienexplorers on 2007-03-22
What is the mount point of /dev/sda.  The mount line should be
sudo mount /dev/sda /(mount point)

example:
sudo mount /dev/sda /media/sda

You would the be able to access sda threw the /media/sda folder.

---

### Post by Pseudo Idol on 2007-03-22
Since /dev/sda1 is not defined in your fstab file you have one of two options:

1. Define it in your fstab file so that when you give the mount command your system knows where to mount it

or

2. When you give the mount command tell it where to mount it like alienexplorers said
mount /dev/sda1 /media/sda1

---

### Post by basilwatson on 2007-03-22
So first create mount point , then tell it where to mount ,?? ( as per wiki I presume ) 

Question why did it change ?? itsbeen fine untill I used it on the laptop  ( was ok with win 2000 , then when I install ubuntu ,,it changed ??) 

Stephen 

thank for the input

---

### Post by basilwatson on 2007-03-22
Thanks to you all I am up and running 

I found  this in my hunt ,,hope it is of some help to others 

Stephen [http://www.smorgasbord.net/book/export/html/195]("http://www.smorgasbord.net/book/export/html/195")

---

### Post by basilwatson on 2007-03-23
Sorry I thought is was solved , on rebooting the next morning the portable usb wouldnt mount  I ve tried  
$ chmod 777 /media/eportable 

followed the wiki on changing the fstab
 for both files and volumes 

followed the above web page for mounting  extra HD

and nothing  

I can mount it  by   $ mount -a   ( in root ) 

but then I only get  to read and execute ,,I can write to it ,,, 

( it works fine with windows xp and ubuntu 6.10 on laptop .....

I tried reformating it as ex3 , with no luck ...


Lost for Ideas ,,anyone ??????

Stephen

---

