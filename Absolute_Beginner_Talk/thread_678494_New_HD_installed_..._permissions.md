---
title: "New HD installed ... permissions"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by circusmonkey on 2008-01-25
Yet again another thread , because I cannot understand the over complicated nature of trying to do something that should be easy just like every other new user to this OS ... 
My drive is installed , its mounted , Ive got the NTFS 3g thingy installed , I can see my drive plus after entering a password I can look at the contents 

I want to blow away the need for entering a password to get onto the partitioned drive , also I would like to be able to create / delete and write to folders to it.

I have tried " sudo chown robert /media/Store"   with no success. I have also used  "sudo nautilus" with which I have had limited success as . I try and enable permissions  but I am told that it is a read only disk ?!?!?. I take it I am supposed to alter the disk in some way but I have not found anything in the help that tells me what to do . 

R

---

### Post by circusmonkey on 2008-01-25
lrwxrwxrwx 1 root root     6 2007-10-11 06:01 cdrom -> cdrom0
drwxrwxr-x 2 root root  4096 2007-10-11 06:01 cdrom0
lrwxrwxrwx 1 root root     7 2007-10-11 06:01 floppy -> floppy0
drwxrwxr-x 2 root root  4096 2007-10-11 06:01 floppy0
drwxrwxrwx 1 root root 16384 2008-01-25 10:54 sda1
drwxr-xr-x 2 root root  4096 2007-10-21 20:14 Store
dr-xr-xr-x 1 root root  4096 2008-01-26 13:26 VideoStore

I can tell my drive is read only !!!!  so how to make it wrx instead of r  ? 

my Fstab looks like this should it help 


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497       38913   107772052+   7  HPFS/NTFS

r

---

### Post by prshah on 2008-01-26
First of all, your mount directory (/media/Store) should belong to the plugdev group, and not "root". use chgrp to change the group.

Secondly, your fstab is not correct; did you set it up by hand or did Ubuntu do it for you? Also would be better if you posted your /etc/mtab.

What I'd suggest is undoing everything that you have done manually, and then let Ubuntu set it up for you by just plugging it in. If nothing happens after you plug it in, check your settings in System->Preferences->Removeable Drives and Media.

Cheers,
PRShah

---

### Post by logos34 on 2008-01-26
> **circusmonkey said:**
> my Fstab looks like this should it help 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497       38913   107772052+   7  HPFS/NTFS

That's fdisk, not /etc/fstab.

Why don't you just install the ntfs-config gui--set the mount point to what you already have and enable write support.  It will edit fstab for your so it automounts at boot, no need for passwords, etc.

sudo apt-get install ntfs-config

gksudo ntfs-config

---

