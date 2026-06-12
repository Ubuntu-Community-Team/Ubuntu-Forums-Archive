---
title: "inaccesible second hard disk"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by bengar on 2007-02-28
After installed ubuntu 6.06 LTS I saw that it was installed on one of my 2 hard disk only, it was installed on the 60 Gb and don't used the second with 300 Gb, I go to disk manager and saw that the second one appear inaccesible, please how can I make available to be used the second one. The fist one said Partition 1, /dev/hda1,  filesystem Extended 3, the access path: /  with a size of 54.47 Gb status accessible and the swap with 1.43 GB  /dev/hda/5, The second one Partition 1, /dev/hdb1, extended 3, access path: none 278 free space not available and the status is inaccessible the swap is the same. Your prompt attention will be appreciated.

---

### Post by the.phantom on 2007-03-01
this might help some?
[http://www.ubuntuforums.org/showthread.php?p=2050511#post2050511](http://www.ubuntuforums.org/showthread.php?p=2050511#post2050511)

i just installed a second hard drive and went through what you went through !

NOTE if you want to partition that drive ( you can do it before it is "mounted"
 you can use QTparted to do it ( in add/remove sysemtools)
after  partitions then you can try what worked for me ?
and i show the drive on the desktop and easy to access now( just like a usb drive)  with a big thanks to Taurus on that one !

---

### Post by the.phantom on 2007-03-01
sorry i am new on this forum and having a bit of cockpit trouble 

before you do what i did above could you please post the results of a 

gksudo gedit /etc/fstab  ( just copy and paste in the terminal)and it will open up a window in a few sec

and also a 
sudo fdisk -l   from the terminal 

thanks don't want to give bad advice

---

### Post by bengar on 2007-03-01
> **the.phantom said:**
> this might help some?
[http://www.ubuntuforums.org/showthread.php?p=2050511#post2050511](http://www.ubuntuforums.org/showthread.php?p=2050511#post2050511)

i just installed a second hard drive and went through what you went through !

NOTE if you want to partition that drive ( you can do it before it is "mounted"
 you can use QTparted to do it ( in add/remove sysemtools)
after  partitions then you can try what worked for me ?
and i show the drive on the desktop and easy to access now( just like a usb drive)  with a big thanks to Taurus on that one !

Phantom
Many thanks, I download QTparted but I can not do nothing, a messege pop up no device  found, maybe you are not using root user?, and close it.

---

### Post by the.phantom on 2007-03-01
qtparted has to be ran in root
so
enter in the terminal

sudo qtparted

and it will launch it and you should be able to do your magic ;-D

---

### Post by dannyboy79 on 2007-03-01
you didn't need qtparted, gparted is there by default. why are you trying to format anything, the install already did that. you just need to add an entry in your fstab so that the folder can get mounted. please post the output from the following commands:

cat /etc/fstab

sudo fdisk -l

then I can help.

---

### Post by bengar on 2007-03-01
> **dannyboy79 said:**
> you didn't need qtparted, gparted is there by default. why are you trying to format anything, the install already did that. you just need to add an entry in your fstab so that the folder can get mounted. please post the output from the following commands:

cat /etc/fstab

sudo fdisk -l

then I can help.


Okay I used qtparted but it don't work. This is the output from the first command line
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       


This the second command line using sudo
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Also I have a second partition of linux frugalware. I want to used the rest of teh free space of the 300 Gb hard disk or used other way like re install ubuntu. Thank you guys for all your attention.

---

### Post by dannyboy79 on 2007-03-01
ah, you posted the same thing twice? according to your post, you stated "The second one Partition 1, /dev/hdb1, extended 3, access path: none 278 free space not available and the status is inaccessible the swap is the same" which to me means that this hard drive was in when you did the install and it formatted it because despite you saying that it is extended 3, i imagine you meant that it's ext3, whish is a filesystem. so just post the output of sudo fdisk -l and we'll take a look to see if it's formatted. although I hope you didn't mess anything up trying to use qtparted. it probably didn't work because you didn't use gksudo or there could be another reason but I can't tell you why.

---

### Post by bengar on 2007-03-01
Yeap danny sorry for the mistake here is all.



> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
bengar@bengar-desktop:~$
bengar@bengar-desktop:~$ sudo fdisk-l
Password:
Sorry, try again.
Password:
sudo: fdisk-l: command not found
bengar@bengar-desktop:~$ sudo fdisk-l
sudo: fdisk-l: command not found
bengar@bengar-desktop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7110    57111043+  83  Linux
/dev/hda2            7111        7297     1502077+   5  Extended
/dev/hda5            7111        7297     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       36294   291531523+  83  Linux
/dev/hdb2           36295       36481     1502077+   5  Extended
/dev/hdb5           36295       36481     1502046   82  Linux swap / Solaris

---

### Post by dannyboy79 on 2007-03-01
ok, add this to your fstab file

/dev/hdb1       /media/whatever ext3    defaults        0       2

i am very curious as to what you have done here? if ubuntu is on hda1 and your ubuntu swap is hda5, and you supposedly have another distro installed somewhere? if you want to be able to boot the other distro, you are going to have to add an entry to your menu.lst file which is located in /boot/grub/. if you just want to use your 300gb hard drive as storage than simply add what I put above. you have to make the directory first, make it whereever you want. you would do sudo mkdir foldername. then if you want to own it do sudo chown yourusername:yourgroupname foldernamehere. then if you want it to be only writable/executable/readbable by you and your group and readable/executable for everyone else you would do sudo chmod 775 foldernamehere. then do sudo mount -a. this will re-read the fstab and mount everything in there.

---

### Post by bengar on 2007-03-01
Okay danny I will try and let you know soon, thank you.

---

### Post by bengar on 2007-03-02
> **dannyboy79 said:**
> ok, add this to your fstab file

/dev/hdb1       /media/whatever ext3    defaults        0       2

i am very curious as to what you have done here? if ubuntu is on hda1 and your ubuntu swap is hda5, and you supposedly have another distro installed somewhere? if you want to be able to boot the other distro, you are going to have to add an entry to your menu.lst file which is located in /boot/grub/. if you just want to use your 300gb hard drive as storage than simply add what I put above. you have to make the directory first, make it whereever you want. you would do sudo mkdir foldername. then if you want to own it do sudo chown yourusername:yourgroupname foldernamehere. then if you want it to be only writable/executable/readbable by you and your group and readable/executable for everyone else you would do sudo chmod 775 foldernamehere. then do sudo mount -a. this will re-read the fstab and mount everything in there.



> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0



Dannyboy
This is what I got just one more thing I c/p this 
**/dev/hdb1       /media/whatever ext3    defaults        0       2**
What I need to write where you wrote whatever

---

### Post by confused57 on 2007-03-03
First, you need to make a mountpoint(make a directory):
```
sudo mkdir /media/whatever
```

You can name the directory "whatever" to something descriptive(/media/data, /media/hdb1)...then change the corresponding mountpoint in /etc/fstab:
/dev/hdb1 /media/whatever ext3 defaults 0 2

Added:  omrsafetyo, thanks for translating...

---

### Post by omrsafetyo on 2007-03-03
> **confused57 said:**
> First, you need to make a mountpoint(make a directory):
```
sudo mkdir /media/whatever
```

You can name the directory "whatever" to something descriptive(/media/data, /media/hdb1)...then change the corresponding mountpoint in /etc/fstab.

translation:

change "whatever" to whatever you want - just make sure that its something that YOU will remember.  

For instance - you could call it /media/300gigdrive

That directory, /media/300gigdrive will be the "mountpoint" for your harddrive - in otherwords, in your filesystem/directory architecture, when you navigate to that directory, Ubuntu will know to use that partition of your 300 gig hard drive.

You could call it anything though...

/media/data
/media/300gigdrive
/media/300gigsofpr0n

etc.

But whatever you choose, you have to create the directory:

sudo mkdir /media/pr0n

then you have to edit /etc/fstab to direct that mountpoint to look at that hdd...

/dev/hdb1 /media/pr0n ext3 defaults 0 2

and you should be all set.

---

### Post by bengar on 2007-03-03
omrsafety

Thank you for your response, let me see whta happend

---

### Post by bengar on 2007-03-03
Thank you everybody now the second hard drive is working, thank you dannyboy, the phanton, and omrsafetyo for all the info. This is a true helper community. **Viva Ubuntu!!!**

---

### Post by dannyboy79 on 2007-03-03
no prob, glad I could help!

---

