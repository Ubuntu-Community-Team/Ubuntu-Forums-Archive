---
title: "[SOLVED] How to install bianary files"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by richsg1 on 2007-08-08
I'm new to Linux and Ubuntu. Been looking through "Windows" too long... I'm ready to go outside and play. I have one computer dual boot with Ubuntu and Windows 2000. First Harddrive with partitions  NTFS, Extended, Fat32, linux-swap, ext3. Harddrive #2 is fat32. I want to be able to share files between OS. Linux won't mount the fat32 drives. Help please.

---

### Post by aquavitae on 2007-08-08
First, you don't need fat32 to share files - look at the ntfs-3g driver.
> Linux won't mount the fat32 drives.How have you tried mounting - i.e. what commands did you use?

---

### Post by richsg1 on 2007-08-09
I have tried to mount. Unable to mount device : error: device /dev/hdb1 is not removable

error: could not execute pmount
. I also tried getting the ntfs-3g driver and got this.

rich@rich-desktop:~$ gksu gedit /etc/apt/sources.list
(gedit:5663): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rich@rich-desktop:~$

Thank you for helping. I really enjoy learning.

---

### Post by be4truth on 2007-08-09
Please paste that into your terminal and post the output here.

```
 sudo fdisk -l
```

---

### Post by AlexenderReez on 2007-08-09
> **richsg1 said:**
> I have tried to mount. Unable to mount device : error: device /dev/hdb1 is not removable

error: could not execute pmount
. I also tried getting the ntfs-3g driver and got this.

rich@rich-desktop:~$ gksu gedit /etc/apt/sources.list
(gedit:5663): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rich@rich-desktop:~$

Thank you for helping. I really enjoy learning.

typo over there
>   ** gksudo **gedit /etc/apt/sources.list

---

### Post by richsg1 on 2007-08-09
rich@rich-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:6717): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rich@rich-desktop:~$

 Thank you. Here's the results.

---

### Post by splintercellguy on 2007-08-09
Ignore the command-line text, it's a known bug. No gedit window pops up?

---

### Post by richsg1 on 2007-08-09
Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        1429     1237005    f  W95 Ext'd (LBA)
/dev/hda3            1430        1826     3188902+  83  Linux
/dev/hda5            1276        1407     1060258+   b  W95 FAT32
/dev/hda6            1408        1429      176683+  82  Linux swap / Solaris

Disk /dev/hdb: 17.2 GB, 17245863936 bytes
255 heads, 63 sectors/track, 2096 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2096    16836088+   c  W95 FAT32 (LBA)

---

### Post by richsg1 on 2007-08-09
Yes, there was a new window pop up. Just looked like error text.

---

### Post by aquavitae on 2007-08-09
> **richsg1 said:**
> I have tried to mount. Unable to mount device : error: device /dev/hdb1 is not removable

error: could not execute pmountWhat command did you use exactly, or what did you click on? It looks like you tried mounting it like you would a flask disk, but that won't work for an internat hard drive. To mount, open a terminal and type the following:
1. First make sure you have somewhere to mount it:
```
sudo mkdir /mnt/hdb1
```
2. Then mount it:
```
sudo mount -o rw,users /dev/hdb1 /mnt/hdb1
```
3. To check that its worked:
```
ls /mnt/hdb1
```
That should work, provided there are no permission problems. Obviously you can change /mnt/hdb1 to whatever path you want - its the location the drive will be mounted.

> 
I also tried getting the ntfs-3g driver and got this.

rich@rich-desktop:~$ gksu gedit /etc/apt/sources.list
(gedit:5663): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rich@rich-desktop:~$

That's a problem with running gedit as root, don't know why, but it seems to happen quite often.  Why do you need to edit that file though?  I thought ntfs-3d was in the normal repos?  You should be able to just install it using synaptic.  If you do need to edit sources.list though, you can do it in a console editor by typing```
sudo edit /etc/apt/sources.list
```
> 
Thank you for helping. I really enjoy learning.
My pleasure!

---

### Post by splintercellguy on 2007-08-09
I believe you can install ntfs-config then use it to automatically add NTFS partitions to the fstab.

---

### Post by richsg1 on 2007-08-09
Aquavitae, Thank you very much. I can now access that drive. Simple code too. One step closer to closing windows.

Problem solved!

---

### Post by igknighted on 2007-08-09
> **richsg1 said:**
> Yes, there was a new window pop up. Just looked like error text.

Nope, thats the file that needs editing.

---

### Post by AlexenderReez on 2007-08-09
> **aquavitae said:**
> What command did you use exactly, or what did you click on? It looks like you tried mounting it like you would a flask disk, but that won't work for an internat hard drive. To mount, open a terminal and type the following:
1. First make sure you have somewhere to mount it:
```
sudo mkdir /mnt/hdb1
```
2. Then mount it:
```
sudo mount -o rw,users /dev/hdb1 /mnt/hdb1
```
3. To check that its worked:
```
ls /mnt/hdb1
```
That should work, provided there are no permission problems. Obviously you can change /mnt/hdb1 to whatever path you want - its the location the drive will be mounted.


That's a problem with running gedit as root, don't know why, but it seems to happen quite often.  Why do you need to edit that file though?  I thought ntfs-3d was in the normal repos?  You should be able to just install it using synaptic.  If you do need to edit sources.list though, you can do it in a console editor by typing```
sudo edit /etc/apt/sources.list
```

My pleasure!

> **richsg1 said:**
> rich@rich-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:6717): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rich@rich-desktop:~$

 Thank you. Here's the results.
>   
sudo nano /etc/apt/sources.list

or

alt + q to exit

> 
sudo vi /etc/apt/sources.list

ctrl + x to exit...

i think you mean this -->
> 
sudo** gedit** /etc/apt/sources.list

sudo is for command line application...gksudo is better in this case :)

---

### Post by aquavitae on 2007-08-10
> 
i think you mean this -->

sudo gedit /etc/apt/sources.list 

sudo is for command line application...gksudo is better in this case :)
No, I meant edit, but after a bit of experimentation I've found it doesn't work as I expected. In gentoo, the command 'edit' automatically runs the default console editor (e.g. vim). I thought it was the same here but apparently not. Apologies!

---

