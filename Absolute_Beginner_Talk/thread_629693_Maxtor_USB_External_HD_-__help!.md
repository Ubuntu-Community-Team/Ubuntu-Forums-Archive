---
title: "Maxtor USB External HD -  help!"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by missed her show on 2007-12-02
hi all, i have a Maxtor OneTouch III USB2 External Hard drive that i'm having difficulty mounting in Ubuntu G.

When i first booted from the Live CD, it recognized the drive and it's contents without any prodding from me.

But then i installed Ubuntu and now i can't Mount the drive. I've followed the suggestions in this thread and still no dice.

Here's the error message:

> $LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sbd1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose 1 action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the windows taskbar then shutdown windows cleanly. Choice 2: If you don't have windows then you can use the 'force' option for your own responsibility. for example type on the command line: Mount -t ntfs-3g /dev/sdb1 /media/New Volume -o force or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/New Volume ntfs-3g defaults, force 0,0

I'm new to ubuntu/linux, decided to ditch windows, so ANY Help would be greatly appreciated. (BTW, the external HD is filled with data....i don't want to have to reformat it.)

thanx for the help

I ran a *sudo fdisk -l* and here is the output:

> Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd835d835

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2372    19053058+  83  Linux
/dev/sda2            2373        2480      867510    5  Extended
/dev/sda5            2373        2480      867478+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000536576 bytes
31 heads, 62 sectors/track, 40648 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Disk identifier: 0x20202020[B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          42       40131    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2              42       40649    39022861    b  W95 FAT32[/B]

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8be2f02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS


again, help is GREATLY appreciated!!

---

### Post by wormser on 2007-12-02
> $LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sbd1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose 1 action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the windows taskbar then shutdown windows cleanly. Choice 2: If you don't have windows then you can use the 'force' option for your own responsibility. for example type on the command line: Mount -t ntfs-3g /dev/sdb1 /media/New Volume -o force or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/New Volume ntfs-3g defaults, force 0,0

This message is giving you 2 options to fix it.  It looks like you removed the drive before using 'safely remove hardware' in Windows.  We need to find out what the name of the mount point is.  Plug the drive in.

```
cd /media
ls -la
```

Look for the name of the folder where the drive mounts.  It will probably be something like maxtor or onetouch.  Next we use the command given to us to use in the error message.  Make sure you put the mount point name.  The red section is where you want to put it.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/**[COLOR="Red"]?Maxtor?[/COLOR]** -o force
```

That should resolve it.  Just remember to unmount your drive before removing it.  From now on it should mount automatically.

---

### Post by missed her show on 2007-12-02
Thanks for the reply.   I'm not sure what i'm looking for, but here's what i got. 
> **wormser said:**
> 
```
cd /media
ls -la
```

Look for the name of the folder where the drive mounts.  It will probably be something like maxtor or onetouch.  Next we use the command given to us to use in the error message.  Make sure you put the mount point name.  The red section is where you want to put it.


Here's what i get:

```
ubuntu@ubuntu:/media$ ls -la
total 0
drwxr-xr-x  2 root root 100 2007-12-03 04:03 .
drwxrwxrwt 30 root root 240 2007-12-03 04:02 ..
-rw-------  1 root root   0 2007-12-03 04:02 .hal-mtab-lock
ubuntu@ubuntu:/media$ 
```

not sure what i'm looking for.

---

### Post by missed her show on 2007-12-02
i realize how rookie i must come off as. 

Well, i rebooted off of the Live CD.   For about 5 seconds, my Maxtor external HD appears on the desktop.   I can browse and see folders and data and everything.   At this point, i right click the drive to Unmount it.    I get an error message saying i can't Unmount,  because /media/.hal-mtab can't be opened.  

I used the mount command you suggested, with the /media/.hal-mtab info, and got the following reply:

```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/.hal-mtab-lock -o force$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sdb1 (New Volume)
ubuntu@ubuntu:~$ 

```

now i can browse the drive again! 

I will attempt to install ubuntu locally (i reformatted the partition on the local disk) and see if this works.   Thanks for the help.

---

### Post by erlyrisa on 2007-12-03
uhh --> I'll post how I go with this --

I was actually considering formating the F-er ext3 ... but nahh, I think I'll keep it as it is.

I went through the exact same process as you describe....

I added the line into /etc/fstab (without force, now that I have mounted once already with -o force and unmounted safely)

but - yeah, I get permission denied when I try and mount/unmount via Nautilus.

I really don't wanna have to stuff around with mounting via sudo everytime I boot.

and what's this other **fuse** thing? - is that how nautilus automounts?


...edit...

I think what's happened is that the -o force option has changed the entire drive into a Root user drive... hence
automount requests from a non root user are impossible.

-I'm thinking maybe plugging it into an XP pc at first would have been advisable (doh) -> it would have initiated the drives user preferences more openly.

-maybe doing a reformat on an XP machine, unplugging it "safely remove hardware" , and plugging it back into the Ubuntu PC could do the trick?

...edit...

I have given up,

--formated EXT - no problems now! -> permissions are set for ME!

---

