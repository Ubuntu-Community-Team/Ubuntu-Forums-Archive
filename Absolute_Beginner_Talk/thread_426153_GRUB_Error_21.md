---
title: "GRUB Error 21"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by johnlil on 2007-04-28
I have installed Ubuntu 7.04 on a USB hardrive. When I reboot I get and error 21 from GRUB and the PC hangs.

The host PC has Vista loaded and I wanted to get a dual boot by using the removable hardddrive.

The only way I can get the machine to boot is by using the Live CD.

Any help greatly appreciated

---

### Post by freebird54 on 2007-04-28
```
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 
```

That is the error you are getting.  From the LIve CD, can you post the output from the following terminal command?

```
sudo fdisk -l
```

That should give us a list of what partitions'disks the system really sees.

---

### Post by johnlil on 2007-04-28
Here you go, thanks for the help

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         196     1574338+  27  Unknown
/dev/sda2             197       30401   242621662+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4665    37471581   83  Linux
/dev/sdb2            4666        4870     1646662+   5  Extended
/dev/sdb5            4666        4870     1646631   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by mikeyphi on 2007-04-28
Try this guide - hope it helps!
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by freebird54 on 2007-04-28
OK.  When you boot, do you get a grub menu - and then the error?  Or does it error and stop right there before you see the menu?

---

### Post by johnlil on 2007-04-28
No  boot menu, just "Loading Grub 1.5", then Error 21

---

### Post by freebird54 on 2007-04-28
This may be the best fix here:  [http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

If this is not enough, then we have to go grub_ing our way by grub command line..

---

### Post by johnlil on 2007-04-28
Thrashing around a bit, thanks for the help so far. I've read through the article, comprehensive but daunting. Here's where I've got to. Any thoughts?

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> 

I was expecting to get the filesystem back as per the article, however now stuck as to what to do next.

---

### Post by freebird54 on 2007-04-28
Now you could try
```

*grub>* setup (hd1)
```

which should give yo someting like:

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+15 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
```


If not - back to devicemap etc

---

### Post by johnlil on 2007-04-28
Tried that, got the same message

GRUB Loading Stage 1.5

GRUB Loading, please wait....
Error 21

---

### Post by freebird54 on 2007-04-28
OK - looking up more sources..... (sounds of electrons flipping)...

---

### Post by freebird54 on 2007-04-28
Here's one possibility:

```
GRUB Error 21 problem solved 

thanks to David Balazic for pointing me in the right direction!
i changed the CMOS settings to detect the HD's in my system...
this is what i did:

entered Standard CMOS Setup

set the Primary Master to:

    Type = User,  Mode = LBA

by scrolling through the options
then set the Primary Slave to:

    Type = Auto, Mode = Auto

 
Hope this helps someone in a similar predicament

 cheers again to David
 

```

Might try that!

---

