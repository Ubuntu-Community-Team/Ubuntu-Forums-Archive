---
title: "Removing Ubuntu - Please!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Hooves on 2007-11-06
Hey there, I need some help.

A friend gave me an 80GB hard drive for free because it had Linux on it and didn't want it, so I took it so I could format it and put a clean copy of Windows on it. I put it in as a slave, and formated it, then put it back in as a master, to see Linux still on it. I've never dealt with Linux before in my life, and I want to get this off the drive. 

From what I read so far, I need to burn Ubuntu on to a CD, then use it to change some partitions back or something. Can someone walk me through this please? Its very confusing being that I didn't install it on the drive to begin with, and I don't have the original boot disk.

It looks like it was dual with XP and Linux on it at the same time, but when I formated it, I got rid of XP. So if theres a way, could I just format a partition? 

By the way, it says its Kernel 2.6.15-26-386, so if I were to get a boot disk to remove this, does it have to be the exact same kernel?

---

### Post by oilchangeguy on 2007-11-06
please explain how you formated the drive. because done properly you would not still have an operating system on the drive.

---

### Post by DJMattB241 on 2007-11-06
Maybe I'm missing something, but couldn't you just pop your XP cd in the computer and boot to it and just have XP's installer wipe the whole drive and essentially start from scratch?

---

### Post by Cannaregio on 2007-11-06
You have to use ANY linux live distribution on your box.
(Knoppix, Ubuntu, whatever)
Then you use gparted

system --> admin --> partition editor

to format whatever you like to whatever format you like, for instance your new disk.

if you really want to use windows on that disk, format to FAT and let then your windows box recognize it.

---

### Post by Hooves on 2007-11-06
> **oilchangeguy said:**
> please explain how you formated the drive. because done properly you would not still have an operating system on the drive.

I got the drive with Linux on it, booted my Windows XP computer up with that drive as a slave, and Formated the drive using Windows format option in My Computer.

---

### Post by Hooves on 2007-11-06
> **DJMattB241 said:**
> Maybe I'm missing something, but couldn't you just pop your XP cd in the computer and boot to it and just have XP's installer wipe the whole drive and essentially start from scratch?

Well, the previous owner of this drive has a copy of Win XP PRO on there, but it wouldn't even boot befor  I formated the drive, and the only XP disk I have is Home.

But after the format, it seems as though it wiped XP off the drive, but not Linux.

---

### Post by Inxsible on 2007-11-06
you can use any software to format it to NTFS. It got rid of XP because that's probably the drive or partition that you formatted. but you probably didnt format the Ubuntu partition.

Format it just the same way you formatted the XP partition and you should have a completely empty NTFS drive (provided you select the NTFS file system).

You would need to either
1) Burn a [Gparted LiveCD]("http://gparted-livecd.tuxfamily.org/") to see the EXT3 partition and format it to NTFS
2) install [fs-driver]("http://www.fs-driver.org") and mount the EXT3 partition and then format it to NTFS.

---

### Post by oilchangeguy on 2007-11-06
> **Hooves said:**
> I got the drive with Linux on it, booted my Windows XP computer up with that drive as a slave, and Formated the drive using Windows format option in My Computer.

you shold not even be able to see the drive in my computer. try going to control panel, admin services, computer mgt, disk mgt. if it shows there, you can format it. if not set the jumper to master, remove or unplug your current drive. and use your windows cd (not a restore cd) to delete the partiton, and create a new partition, and format it to ntfs.

---

### Post by poudin on 2007-11-06
using the windows XP should have formatted the HDD on install...that being said...if it didnt work and you want to wipe the drive try this program

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

this will wipe the drive 100% guaranteed...than you can install from scratch...we use this program at work to wipe drives before with Recycle them with an external company so that no data can be recovered...good luck with the reinstall

---

### Post by volksman on 2007-11-06
it is likely the MBR still remaining after the format.  Use GParted live CD and wipe the partitions and MBR.  Should be fine after that.

---

### Post by maybeway36 on 2007-11-06
Wiping MBR with DOS:
```
fdisk /mbr
```
Wiping MBR with Linux Live CD (assuming your hard drive is IDE primary master):
```
dd if=/dev/zero of=/dev/hda bs=1 count=446
```

---

