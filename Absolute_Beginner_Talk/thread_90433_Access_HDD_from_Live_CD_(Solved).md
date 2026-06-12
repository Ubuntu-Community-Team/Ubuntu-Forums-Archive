---
title: "Access HDD from Live CD (Solved)"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Decon1 on 2005-11-14
Greetings all!

I have just started to play with Linux and Ubuntu.  Burned the ISO to the CD boots with no problems.  Very nice!

I am trying to get access to my HDD.  I went to System, Administration, Disks, Hard Disk, Partitions.  In status it says inaccessible with an Enable button highlighted and the Browse button Greyed out.  Here's where I "chickened out" :rolleyes:   If I press the Enable button will I have access to my HDD?  More importantly will I change anything in my Windows XP setup?  I have to be sure!  I'm not ready to kill XP.

Thanks for the info.  OBTW, Ubuntu seems the best of all the Live CDs i have tried!  very nice.

Regards,
Decon1

---

### Post by Samuel on 2005-11-15
well i just tried doing what you said but it didnt do anything for me,
you could open a terminal and type
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
this should make an icon of a disk on your desktop, it will be read only so it wont effect the Windows XP partition. 

in the code im assuming your XP partition is on the first partition of the first hard drive, and that its using NTFS file system (these are bot hdefaults for windows xp)

also bear in mind that a real install runs much faster, and can resize your xp partition to make room for itself and duel boot so you have a choice of which operating system you want to use :)

Hope this helps clear things up a little

---

### Post by aysiu on 2005-11-15
[QUOTE=Samuel]
in the code im assuming your XP partition is on the first partition of the first hard drive, and that its using NTFS file system (these are bot hdefaults for windows xp)[/quote] To be sure it is /dev/hda1, type ```
sudo fdisk -l
``` in the terminal and find out.

> 
also bear in mind that a real install runs much faster, and can resize your xp partition to make room for itself and duel boot so you have a choice of which operating system you want to use :) [Here's a great guide for doing that](http://users.bigpond.net.au/hermanzone/)

---

### Post by Decon1 on 2005-11-15
Thanks to both of you!  Samuel...do I have to type that in each time I run Live CD?

Thanks again,
Decon1

---

### Post by audax321 on 2005-11-15
Well, I'm not Samuel, but yes you do. A LiveCD is loaded to and run from memory so when you reboot all your settings are erased. Some distros let you save configuration data to usb storage devices, but I don't think Ubuntu's LiveCD does. The Ubuntu LiveCD is nice but, in my opinion is meant more to try the OS before installing it so that is why they haven't bothered adding the functionality.

---

### Post by Decon1 on 2005-11-15
audax321

Hehhehe!  No problem! Thanks
D

---

### Post by teaker1s on 2005-11-15
how do you mount ubuntu hd primary master with live cd to repair your damaged system?

---

### Post by audax321 on 2005-11-16
[QUOTE=teaker1s]how do you mount ubuntu hd primary master with live cd to repair your damaged system?[/QUOTE]

Pretty much the same way:

Create a directory to mount in:
[INDENT]sudo mkdir <path to directory you want to mount>[/INDENT]

Mount the partition:
[INDENT]sudo mount /dev/hda1 <path to directory you want to mount>[/INDENT]

If its a linux partition, I normally just leave all the -t and -o options out because it normally mounts it with defaults anyway.

To unmount:
[INDENT]sudo umount <path to directory where you mounted the partition above>[/INDENT]

:) Again make sure to check (sudo fdisk -l) to see if /dev/hda1 is the right device and partition.

---

### Post by Decon1 on 2005-11-18
Ok tried this last night and it would not work??  Opened a Terminal and at that demo@tty1[~]$ thingy.  I typed that in.  Is it two lines or typed all on 1 line?

Thanks!
Decon


[QUOTE=Samuel]well i just tried doing what you said but it didnt do anything for me,
you could open a terminal and type
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
this should make an icon of a disk on your desktop, it will be read only so it wont effect the Windows XP partition. 

in the code im assuming your XP partition is on the first partition of the first hard drive, and that its using NTFS file system (these are bot hdefaults for windows xp)

also bear in mind that a real install runs much faster, and can resize your xp partition to make room for itself and duel boot so you have a choice of which operating system you want to use :)

Hope this helps clear things up a little[/QUOTE]

---

### Post by MichaelM on 2005-11-18
[QUOTE=Decon1]Ok tried this last night and it would not work??  Opened a Terminal and at that demo@tty1[~]$ thingy.  I typed that in.  Is it two lines or typed all on 1 line?

Thanks!
Decon[/QUOTE]
It is two lines. Did you get any error message?

---

### Post by Decon1 on 2005-11-19
Still could use more help here??

sudo mkdir /media/winxp
sudo mount /dev/sda1 /media/winxp -t ntfs

The above works and the HDD appears on the desk top.  If i click on it it says I don't have permission because I'm not the owner......So under users and groups I create decon and in terminal type:

sudo chown decon /media/winxp

Then: "run as another user" select decon

<Sigh> it all appears to go well but I still must do the Sysytem, Admin, Disks to access this?

LOL!!  This is acting like Windows :confused:

---

### Post by MichaelM on 2005-11-19
It looks like you didn't put in the "nls=utf8,umask=0222" part. I'm not sure what "nls=utf8" means (I think it has something to do with character sets), but "umask=0222" is what lets you access your HD as someone other than root.

---

### Post by Decon1 on 2005-11-22
Ok here now!  Had to issue the mount command twice!

I now have it installed in VMware.  Dual boot to come soon!

---

