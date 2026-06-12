---
title: "Hotplug Thumb Drive fails"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by palmdoc on 2006-01-28
Hi. I tried searching in the forums for the solution but being a noob, I don't understand much of the discussion and solutions.
Basically none of my thumb drives seem to be recognized when I hotplug them in my Desktop running Ubuntu Breezt 5.10

dmesg | tail as suggested gives this error message:

> [4295077.796000] VFS: Can't find ext3 filesystem on dev sda.
[4295077.807000] VFS: Can't find ext3 filesystem on dev sda.
[4295077.818000] VFS: Can't find an ext2 filesystem on dev sda.
[4295077.829000] VFS: Can't find an ext2 filesystem on dev sda.
[4295077.848000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4295077.868000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4295077.883000] XFS: bad magic number
[4295077.883000] XFS: SB validate failed
[4295077.897000] XFS: bad magic number
[4295077.897000] XFS: SB validate failed

Where do I go from here?
This is a vital step in my migration from Windows XP to Ubuntu Linux, If it fails, then I'm afraid I have to abandon the Linux ship....

---

### Post by mgmiller on 2006-01-29
I use a 1 gig thumb drive in ubuntu 5.10 a lot without problems.  

It looks like your machine is looking for a valid file system on the thumb drive and not finding one.  Most thumb drives are formatted in fat32 which is readable/writable by all OS's.  Fat32 is natively supported by the current kernel in ubuntu linux.  

Are you sure these drives are formatted?  Do they work in windows XP?  If they do, what file system does windows say is on them?  

If there is nothing of importance on the thumb drives, try reformatting them in fat32.  This can be done in Linux, but is sometimes buggy with windows file systems, it may create fat16 instead of fat32.  It's real easy to format it on a windows box. (I hate to say that, but the object here is to get you up and running with as little hassle as possible)

I also assume we are talking about thumb drives, not memory cards like SD or XD or similar, although these are also normally formatted in fat32 by the camera that uses them.  You would use the camera to reformat the card.

You can also try in your machines BIOS looking for an entry for "legacy USB support"  or similar wording and if it is enabled, disable it.  This fixes weird USB bugs in both windows and Linux. 

One last thought, have you tried diffrerent usb ports on the ubuntu machine?  Sometimes, the front ports don't work for some things and the ports on the back of the machine do.  (It has to do with the power requirements of the USB device and also sometimes the fronts are not USB 2.0.  Not really a Linux problem, have it with windows also.)

Hope this helps.

---

### Post by palmdoc on 2006-01-29
Thanks for the reply. The devices are formatted in FAT16 and not FAT32. I'll try reformatting in FAT32 and give it a go again.
My main Hotplu device which I hope to get working is Card Export II and the Treo 650's SD which is unfortunately still in FAT16

---

### Post by palmdoc on 2006-01-29
All the thumbdrives and USB ports work in XP which I have dualbooted as an option. 
As for FAT16 I can't change that to FAT32 for the Treo650 since the Treo only supports FAT16. From my searches in the forum, Linux/Ubuntu should support FAT16. 
Any other clues?

---

### Post by ]Nbx*cmD[ on 2006-01-29
Have you tried mounting the device from the console?

```

sudo mkdir /mnt/flashdisk
sudo mount -t vfat /dev/sda1 /mnt/flashdisk

```

---

### Post by palmdoc on 2006-01-29
Is "flashdisk" generic or what should I put it for the name of the device plugged in?
I see my Thumb drive as Luwen EasyDisk

I did try it reformatted to Fat32 but still no go.

---

### Post by palmdoc on 2006-01-29
OK, this time opening up the Computer drives view and trying to open the Thumbdrive gives this error:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

I then tried 

```

sudo mkdir /mnt/EasyDisk
sudo mount -t vfat /dev/sdb /mnt/EasyDisk
```


I am getting this error message:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

palmdoc@DaddyUbuntu:~$ dmesg | tail
[4295392.927000] scsi0 (0:0): rejecting I/O to dead device
[4295392.927000] FAT: Directory bread(block 2027) failed
[4295393.928000] scsi0 (0:0): rejecting I/O to dead device
[4295393.928000] FAT: Directory bread(block 2024) failed
[4295393.928000] scsi0 (0:0): rejecting I/O to dead device
[4295393.928000] FAT: Directory bread(block 2025) failed
[4295393.928000] scsi0 (0:0): rejecting I/O to dead device
[4295393.928000] FAT: Directory bread(block 2026) failed
[4295393.928000] scsi0 (0:0): rejecting I/O to dead device
[4295393.928000] FAT: Directory bread(block 2027) failed



The reformatted fat32 256 MB thumbdrive works under XP..... :cry:

---

### Post by palmdoc on 2006-02-08
No other clues anyone?
Sadly that means I have to resort back to Windoze.......

---

### Post by 111787 on 2006-02-08
I have literally the exact same problem but my flash drive was working then i unplugged it and plugged it back in now it wont read.

---

### Post by palmdoc on 2006-02-19
Bump. Any additional guidance and tips from experienced Ubuntu users would be most welcome here.
Its sad that the thumbdrives work under Windows but fail to do so with Ubuntu.
Why? :confused:

---

