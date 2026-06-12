---
title: "[SOLVED] Mounting Pri/Mstr while under LiveCD"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-18
Running LiveCD and trying to copy file from /home to usb drive.


On attempted mount of pri/master I got a hal no mount policy error (see attached screenshot).

How can I mount this pri/master and copy the /home over to a usb harddrive?

---

### Post by taurus on 2007-12-18
Is /home on it own partition and what is it anyway?  See if you can mount it from a terminal?

```
sudo mkdir /mnt/home
sudo mount -t ext3 **/dev/sda3** /mnt/home
```
Replace /dev/sda3 with the actual partition.

---

### Post by Mark_in_Hollywood on 2007-12-18
I'm trying to move the /home from the 40 gig to the 20 gig. I know it will fit.

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2040    16386268+  83  Linux
/dev/sdb2            2307        2434     1028160    5  Extended
/dev/sdb3   *        2041        2306     2136645   83  Linux
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
/dev/sdb6            2307        2327      168619+  82  Linux swap / Solaris

---

### Post by Mark_in_Hollywood on 2007-12-18
I tried:

ubuntu@ubuntu:~$ sudo mkdir /mnt/home
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/home

but I can't get the Gnome Desktop (right click on drive icon) to copy /home (sda1) to /home (sdb1) or some such.

I do see the /home (pri-mstr) I'm trying to either copy (safer) or move to the 20 gig usb drive.

---

### Post by Mark_in_Hollywood on 2007-12-18
Folks:

I have tried to figure it out. I have changed the file permissions as some of the folders in /home (to be copied or moved) were set as root only. Yet, I still cannot get the files to move. I'm more than willing to try the command line. for the life of me, I don't know what the usb drive is called or what commands move files into it. 

Additionally, why doesn't selecting folders from within /mnt/home allow me to move or copy them as well?

I can highlite folders I want to copy or move, but when I try to paste them int /home (or somewhere else in the filesystem) I get a permission error. I tried gksudo nautilus to copy, too, but no success.

---

### Post by x-to-tha-t on 2007-12-18
try opening a terminal and using
```
dmesg
```
and see what it comes up with - that should tell you what the /dev/ location of the USB drive is (in amongst the useless info). Then use the command:
```
sudo mkdir /media/usbdrive
```
Replace usbdrive with whatever name you want. Do you know that the filesystem on the USB drive is a linux native (ie Ext2 or Ext3)? Once you know that you should be able to use the command:
```
sudo mount /dev/sdc -t partititiontype /media/usbdrive
```
Replacing sdc with the location of the USB drive and partitiontype with ext2,ext3,ntfs or whichever filesystem it uses and usbdrive with the name of the directory you created, Then use the command:
```
sudo chmod 777 /media/usbdrive
```
replacing usbdrive as before, to make the mounted partition read/write for all users. Then you should just be able to drag and drop. If not try using the mv command. For more info on it go to a terminal and type:
```
man mv
```
Hope this helps.

---

### Post by Mark_in_Hollywood on 2007-12-18
Yikes! 

way too much output from dmsg.

Let me ask another way. I have the pri/mstr mounted. 

How do I mount the usb drive (which is a 20 gig disk)? 

That drive, which shows an icon labeled disk-1 on the desktop, seems to be mounted under the LiveCD, but maybe not to the primary-master, so how do I mount it so that I can move or copy files across?

---

### Post by x-to-tha-t on 2007-12-18
To decrease the amount of info which dmesg gives try:
```
dmesg | grep /dev/
```
Any drives will show up as /dev/sd(a-h) (e.g./dev/sdd) or /dev/hd(a-h).
Ah right - if it is mounted already it will be mounted under /media/disk-1 if that is how it appears on the desktop. Open a terminal and try:
```
cd /media/

ls -l
```
This should show you a directory called disk-1. The permissions are listed on the left it should say something along the lines of drwxrwxrwx. If any of this set shows as a - then your permissions are wrong. To fix that use:
```
sudo chmod 777 /media/disk-1
```
This will fix the permissions problem. In my copy (just standard install) the directory shows up in blue lettering on green background in terminal when permissions are ok. ls is the command to show the contents of a directory (sorry if you already know - don't mean to condescend)

---

### Post by Mark_in_Hollywood on 2007-12-18
[QUOTE=x-to-tha-t;3975774]try opening a terminal and using
```
dmesg
```
and see what it comes up with - that should tell you what the /dev/ location of the USB drive is (in amongst the useless info). Then use the command:

the output of dmesg has only three mentions of a /dev

[  116.873748] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[  116.886103] Adding 859436k swap on /dev/sdb5.  Priority:-2 extents:1 across:859436k
[  116.898281] Adding 168608k swap on /dev/sdb6.  Priority:-3 extents:1 across:168608k

I see nothing about usb. This is not a usb memory stick, it is a 20gig harddrive in a usb cradle. It is seen as mounted by the LiveCD session, but I can't write to it.

At the moment, I am running under a LiveCD session, I have a 40 gig drive as primary master and a 20 gig as a usb storage device. Both of these devices appear in Places/Computer. Both say they are mounted. There are desktop icons for them as well. ALL I want to do is copy my 40gig's /home to the 20 gig/s /home. Both drives are ubuntu, the 40 gig may be Feisty (I've forgotten) and the 20 gig is gutsy.

---

### Post by x-to-tha-t on 2007-12-18
I'd say the likelihood is that you have a permissions issue. Check the ls -l in both /home directories in a terminal (your standard ie /user/home/ and your other drive it will be in /media/disk-1/user/home (replace user with your username)) and if any of the permissions indicators (see my last post) come up as - then that's going to be your problem. If you have any problems with this post back and I'll talk you through it step by step - the command line can be quite daunting.

---

### Post by Mark_in_Hollywood on 2007-12-18
Yes sir! It is a permissions issue, but the problem is that these two disks, are running under a LiveCD session, so the command line isn't helpful here, unless you can tell me how to find these devices. They don't show up in the LiveCD filesystem. Even though they seem mounted to the LiveCD desktop, they aren't mounted in the usual meaning of the word. I guess if they were mounted, and I was logged in user sudo, it would be a snap.

More ideas, please.

---

### Post by x-to-tha-t on 2007-12-18
I take it there is no way you could boot from either of the drives? If not then I'm stumped I'm afraid mate. I'm thinking because / is not mounted read/write that you may not be able to. Sorry! If you check your BIOS settings, you may be able to boot from USB if that's the limiting factor - most modern MoBos can.

---

### Post by Mark_in_Hollywood on 2007-12-18
OK, give me a moment to power down & reboot. I'll be right back!

---

### Post by Mark_in_Hollywood on 2007-12-18
I'm ready to rock!

---

### Post by x-to-tha-t on 2007-12-18
Are you booted to HDD? Also is the other drive mounted as disk-1 as before?

---

### Post by Mark_in_Hollywood on 2007-12-18
The computer is running form a pri/slave Gutsy. The bios boots to the slave first. At the moment, the 40 gig drive does not show in Places/Computer. It probably has to be mounted. but I'm guessing.

---

### Post by 720iD on 2007-12-18
try clonezilla. it boot and run will run from ram.

---

### Post by Mark_in_Hollywood on 2007-12-18
Thanks, mate, I'll have a look at it. But for the record, the 40gig that sits as pri/mstr has several grub errors and won't boot. I only want to bring the /home across from it to the 20 gig. I know the approx. size of the /home on the 40 gig to be about 10 gig. so there is room emough.

---

### Post by 720iD on 2007-12-18
clonzilla is defintiely what your after. it will clone the drive and copy the clone to another drive that is connected while running from live cd or ram. choose at boot.

---

### Post by x-to-tha-t on 2007-12-18
Well first up we need to find out where that drive is. To do this use the command:
```
sudo fdisk -l
```

This will tell you all the drives attached to the computer. By the sizes shown you should be able to tell which one is your 40Gb. The partition you need to use is the one with the ID of 83 (I think!). To mount it you first need to create a directory for it:

```
sudo mkdir /media/40gb
```

Use whatever you like instead of 40gb. Then you need to mount it to that directory.

```
sudo mount /dev/hda1 -t ext2 /media/40gb
```

Replace hda1 with the partition which had ID 83 and ext2 with the relevant filesystem and 40gb with whatever you called the new directory. This should then have mounted the drive. Then you need to go to the drive and sort out the permissions:

```
sudo chmod 777 /media/40gb
```

This should sort out all of your permissions problems. You may need to do this for all directories you're wanting to copy into. Then you *should* be able to just drag and drop. If not, try using the mv command (man mv for details), then try changing the permissions on your home directory - I'd be lying if I told you I knew how to change it back off the top of my head but I found a website you could use... [http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

Hope all this helps mate!

---

### Post by Mark_in_Hollywood on 2007-12-18
Thanks. While I was fooling with all this, I was able to copy the files from the 40gig's /home to the 20 gig's /home/Desktop. The permissions problem seems to have vanished into thin air (go figure!). I'm about to dismantle the computer, put the 20 gig back in the usb cradle and move that /home's files to the 320 gig.

Thanks, Community &

Merry Christmas

---

### Post by x-to-tha-t on 2007-12-18
Glad to be of help!

---

