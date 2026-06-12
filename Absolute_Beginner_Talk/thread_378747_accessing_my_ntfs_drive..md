---
title: "accessing my ntfs drive."
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-07
Okay so I have two hard drives. hda/hdb. I done a clean install of Ubuntu Edgy on hda but I have all my music,etc on hdb which is ntfs.

I've done 

mkdir -p /ntfs
mount -t ntfs /dev/hdb1 /ntfs

but when I try to go into the /ntfs folder I get a insufficient permissions error.


Cheers.

---

### Post by mand0 on 2007-03-07
You need to install a driver for NTFS partitions.

Follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by auraithx on 2007-03-07
Okay it all worked fine, and I Set the mound point as "HD" 

now when I go into /dev/hdb1 I still cant open it?

---

### Post by mand0 on 2007-03-07
Did you do a full reboot?

---

### Post by auraithx on 2007-03-07
At the time I hadn't, now I have an I still have the same problem.

I tried mounting it again and this time it autocompletes to media/mount for the mount point. but I checked there and theres nothing there either :(

---

### Post by mand0 on 2007-03-07
Are you mounting just through the Terminal or are you editing your fstab?

---

### Post by auraithx on 2007-03-07
Uhh, neither. I just followed the tutorial and then used the program thats in Applications --> System Tools --> NTFS Config. tool

---

### Post by mand0 on 2007-03-07
Type this in the Terminal:

```
gksu gedit /etc/fstab
```

At the very bottom you want to add:

```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```

Make sure to add your correct partition and mount point.

Oh, and don't forget to reboot :D

---

### Post by i0Null on 2007-03-07
[SIZE="2"]It sounds like a permission problem. When your system mounts the NTFS partition, look to see if you can see any files with a root browser ("gksudo nautilius"), and if there is: umount the file system and remount it:

```

umount /dev/hdb1
ntfs-3g /dev/hdb1 /ntfs -o umask=0022

``` [/SIZE]

---

### Post by Saul Zaddik on 2007-03-07
Hi auraithx ,

I am not a Windows, or Ubuntu, expert. So read my advice with the eye of a skeptic. 

I found that by adding myself as a user on my XP machines I could access all of the drives on my XP machines. I added Ubuntu user name to my XP machines with the same password I used to log on the Ubuntu machine. I then added my new Ubuntu matching profile to each drive on the XP machines as a user with read and write privileges (I restrict access to the drives and folders on the XP machines to different users and groups). I found after doing this I could see the drives when I browsed for the machines and drives under places in Ubuntu. 

I am writing this from an XP machine and can not look at the exact Ubuntu desktop. I followed the instructions found here in the Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide at [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) to mount the drives. 

The Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide will tell you how to mount the visible machines and drives the way you want to. It is, I have found, an excellent source of information. I think you will be able to access your NTFS drive at boot with ease.

I hope this helps without offending.

Saul

---

### Post by auraithx on 2007-03-08
```
glasgowm@glasgowm-desktop:~$ umount /dev/hdb1
umount: /dev/hdb1 is not mounted (according to mtab)
glasgowm@glasgowm-desktop:~$ ntfs-3g /dev/hdb1 /ntfs -o umask=0022
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
glasgowm@glasgowm-desktop:~$ ntfsfix
bash: ntfsfix: command not found

```

okay, so I installed ntfsfix. now I get this error

```
root@glasgowm-desktop:/home/glasgowm# ntfsfix /dev/hdb1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr... 
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... FAILED
Error setting volume flags.


```

---

### Post by auraithx on 2007-03-08
bump

---

### Post by auraithx on 2007-03-08
Woo! I have no idea how this worked but I ended up having to re-install Ubuntu, upon restarting hdb1 was sitting on my desktop :guitar:

---

