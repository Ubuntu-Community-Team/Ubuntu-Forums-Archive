---
title: "Using Live CD to access broken Ubuntu files"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-07-14
I managed to break my ubuntu setup after using gparted to move stuff around.  I want to use the live CD to access some files from the hard drive to back them up before I reinstall it.  I was able to mount each of the drives I wanted to access, one to copy files from, and one to save files to.  I mounted one to /mnt/ and the other to /media.  However, when I try to copy and paste the files I want (really my home directory), it says I don't have permission to write to /media.  

The problem started after movies partitions around to give more room, and now when ubuntu  boots, it says my home directory can't be found.  I either need help to fix my home directory, or help to salvage my files before I reinstall.  

I am a newbie, so please don't assume I know what you're talking about.  In other words, speak plainly.  

I want to copy my home directory (or at least some of the files from it from hda8 to hda5.  See fdisk info below.  Thank you.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/hda2            4463       19929   124238677+   f  W95 Ext'd (LBA)
/dev/hda5            4463       11551    56942361    b  W95 FAT32
/dev/hda6           11552       11563       96358+  83  Linux
/dev/hda7           11564       13387    14651248+  83  Linux
/dev/hda8           13388       15211    14651248+  83  Linux
/dev/hda9           19687       19929     1951866   82  Linux swap / Solaris

Disk /dev/hdb: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2534    20354323+   b  W95 FAT32
ubuntu@ubuntu:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by bobplano on 2007-07-14
there are a few ways to backup your files. the easiest way would probably rsync:
```
rsync -av /home/you /media/harddrive
```
or you could just use 
```
gksudo nautilus
```
and then use copy paste. 
i don't know how to fix the partitions, i did this before and i just reinstalled

---

### Post by confused57 on 2007-07-14
Your UUID's have probably changed on the partitions that you have resized...you can boot up the live cd, open a terminal, enter:
```
blkid
```
this will show your current partition filesystem UUID's

Then you will need to mount your root partition, open your /etc/fstab, then copy & paste the correct UUID's from "blkid" into your fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You might want to check the kernel line root UUID in your menu.lst also.

---

### Post by thefoolisme on 2007-07-14
Using gksudo nautilis didn't work.  It still says I don't have permission.  

Typing blkid into terminal didn't do anything.  it just went back to the prompt.  WHile the link provided seems very informative, I think I'm too much of a noob to understand what they are really saying. 

Can someone please help me save my home folder?

---

### Post by confused57 on 2007-07-14
> **thefoolisme said:**
> Using gksudo nautilis didn't work.  It still says I don't have permission.  

Typing blkid into terminal didn't do anything.  it just went back to the prompt.  WHile the link provided seems very informative, I think I'm too much of a noob to understand what they are really saying. 

Can someone please help me save my home folder?
I don't know why "blkid" didn't show anything...you can try mounting your hda5 & hda8:
```
sudo mkdir /media/home
sudo mount -t ext3 /dev/hda8 /media/home
```

then mount your data partition:
```
sudo mkdir /media/data
sudo mount /dev/hda5 /media/windows -t vfat -o umask=000
```

Copy & paste the above into a terminal...then you should be able to open Nautilus, navigate to your /media folder and open your home & data directories...then drag & drop files from your home to data.

---

### Post by thefoolisme on 2007-07-15
I was able to rescue the files I wanted, so thanks.  :-)  

As for fixing it so Ubuntu boots correctly, I think that's beyond this newbie's scope, so I'm going to reinstall, and set it up again.  I'll have to learn about saving the home directory another time, and I've learned my lesson about messing with the partitions.

---

### Post by antoz on 2007-07-15
**confused57**

Good to see you are still out there helping, cheers, A.

---

