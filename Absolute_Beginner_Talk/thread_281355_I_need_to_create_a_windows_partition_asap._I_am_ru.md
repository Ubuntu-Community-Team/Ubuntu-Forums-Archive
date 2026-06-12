---
title: "I need to create a windows partition asap. I am running linux only currently."
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by anony on 2006-10-20
Hello everyone. I have a 250gb hd hard drive. Currently, it is only running ubuntu drapper. I need to convert this current partition to fat32 or ntfs so I can install windows. Windows does now recognize the drive as /dev/hda1 is partitioned for linux. How can I change this partition so it is fully read/writable with windows?
Thanks

---

### Post by aysiu on 2006-10-20
Do you have a live CD handy?

---

### Post by anony on 2006-10-20
I mis-placed my ubuntu disk. Would the fastest option be to re-download ubuntu and use the live-cd?

---

### Post by aysiu on 2006-10-20
Yes, you would need a live CD to do this.

---

### Post by anony on 2006-10-20
Once I download the live-cd, how can I do this?

---

### Post by pay on 2006-10-20
Are you trying to wipe out linux and have only windows or dualboot? hda1 most probbably is your root linux partition or a boot partition so if you want to keep linux you shouldn't wipe it clean.

---

### Post by aysiu on 2006-10-20
You'd boot up the live CD and then press Alt-F2.

From that, a **Run** dialogue will pop up. In that dialogue, type ```
gksudo gparted
``` With GParted, you can delete your Ubuntu partition and create an NTFS or FAT32 partition.

If, for some reason, GParted doesn't start or the command isn't found (I believe it comes standard on a live CD, but I'm not 100% sure of that), you can install it easily with these [terminal](http://www.psychocats.net/ubuntu/terminal) commands: ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` [http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by anony on 2006-10-21
> **aysiu said:**
> You'd boot up the live CD and then press Alt-F2.

From that, a **Run** dialogue will pop up. In that dialogue, type ```
gksudo gparted
``` With GParted, you can delete your Ubuntu partition and create an NTFS or FAT32 partition.

If, for some reason, GParted doesn't start or the command isn't found (I believe it comes standard on a live CD, but I'm not 100% sure of that), you can install it easily with these [terminal](http://www.psychocats.net/ubuntu/terminal) commands: ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` [http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Ok, gparted starts fine. I then deleted my ubuntu partition. Next I add a ntfs partition and set it as the primary. So I have only 1 partition listed (set as ntfs). I then stick in my windows install disk and go to the install point and it still doesn't recognize the disk. What should I do?
Thanks.

---

### Post by anony on 2006-10-21
Any ideas, any one?
Thanks for your help,
anony

---

### Post by point6 on 2006-10-21
hello.

There is some problem with using windows in some of the hhd's.
If you have an SATA hdd you need to install some drivers before installing the OS. The same is fore some IDE hdd's.

To do this you will need to download SATA drivers for your motherboard (or hdd if you have an IDE disk), put it on an floppy disk (for some reason CD/dvd/flash dosent work).
When you are done you need to load the drivers into the RAM trough the installing wizzard for windows, you will need to press an "F" key.. F6 or something.. it should say "Press F6 to install SCASI something something".

It should fix the problem.

It feel strange that my first post on this Ubuntu forum is about Windows =).

---

### Post by Sef on 2006-10-21
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to learn how to install both Windows and Ubuntu on one harddisk.

---

### Post by anony on 2006-10-21
> **Sef said:**
> Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to learn how to install both Windows and Ubuntu on one harddisk.

All I am looking to do is make this drive readable by windows so I can install windows again. I currently have 0 partitions on it but it is only readable by linux. How can I change this?

---

### Post by az on 2006-10-21
> **anony said:**
> All I am looking to do is make this drive readable by windows so I can install windows again. I currently have 0 partitions on it but it is only readable by linux. How can I change this?

Use cfdisk (or fdisk) and tell it to write a blank partition table.

Parted and linux are more capable of handling a corrupt (non standard) partition table than windows.  Windows only really recognizes it's own filesystems anyway.

---

### Post by catlett on 2006-10-21
Download a dos bootdisk from here [http://www.bootdisk.com/](http://www.bootdisk.com/) At the prompt enter ```
FDISK
```The interface is pretty intuitive.

---

### Post by anony on 2006-10-21
Point6, I don't have a floppy drive ](*,) 
Also, I downloaded a dos boot disk and then I set up a partition while booting from that disk. When I went to save my changes it said I can not create an MDB file. I deleted this before by accident. Is there anyway I can re-create this in gksudo? What else can I do to get this drive recognizable by windows?

---

### Post by anony on 2006-10-21
Also, when I am on gparted in linux my fat32 partition (my only partition) says unmounted when I click it then go into information. Do I need to mount this? If so, how can I do that?

---

### Post by catlett on 2006-10-21
> **anony said:**
> Also, when I am on gparted in linux my fat32 partition (my only partition) says unmounted when I click it then go into information. Do I need to mount this? If so, how can I do that?

to use gparted the partition has to be unmounted. Leave it unmounted and delete it. Then format it again as a fat32 primary partition. Make sure to hit "apply" after the operations. Windows should be able to see fat32 partition without issue. Fat32 was the file system used for windows before XP. Maybe there was an issue with the last time gparted formatted it. I would try re-formatting it again, you have nothing to loose and it will only take a few minutes. Maybe you'll get lucky.

---

### Post by anony on 2006-10-21
> **catlett said:**
> to use gparted the partition has to be unmounted. Leave it unmounted and delete it. Then format it again as a fat32 primary partition. Make sure to hit "apply" after the operations. Windows should be able to see fat32 partition without issue. Fat32 was the file system used for windows before XP. Maybe there was an issue with the last time gparted formatted it. I would try re-formatting it again, you have nothing to loose and it will only take a few minutes. Maybe you'll get lucky.

It is still not read by windows. Are there any other options?
Right now my gparted has 2 partitions.
unallocated which is 7.84mb
and
/dev/sda1 fat32 232.88gb and it says it has 116.42 mb used... i just formatted and re-created this how does it have space used?
What should I do?

---

### Post by anony on 2006-10-21
Also, my disklabel is set as msdos, should I change this?

---

### Post by tubasoldier on 2006-10-21
You have an SATA hard drive. Some windows installers do not recongnize these disks. Point6 did a very good job of pointing this out. You will either have to figure out a way to load the driver for the disk so windows can recognize it or get a newer build of Windows XP. XP disks that shipped with SP2 have these drivers on them already.

---

### Post by anony on 2006-10-21
> **tubasoldier said:**
> You have an SATA hard drive. Some windows installers do not recongnize these disks. Point6 did a very good job of pointing this out. You will either have to figure out a way to load the driver for the disk so windows can recognize it or get a newer build of Windows XP. XP disks that shipped with SP2 have these drivers on them already.

I have an IDE drive. Are there any places to get good generic IDE drives that I can install without having windows running (through dos or something)?

---

### Post by tubasoldier on 2006-10-21
> **anony said:**
> 
/dev/sda1 fat32 232.88gb and it says it has 116.42 mb used... 

Sorry, this gave me the impression that it is a SATA drive. /dev/sda usually points to SATA or USB drives.

---

### Post by anony on 2006-10-21
> **tubasoldier said:**
> Sorry, this gave me the impression that it is a SATA drive. /dev/sda usually points to SATA or USB drives.

If I re-install ubuntu and then uninstall it correctly would that fix this issue?

---

### Post by anony on 2006-10-22
Is there any way to do this or am I screwed with a drive that I can't install windows on?

---

### Post by Bartender on 2006-10-22
anony - 
Don't panic.  If all you're trying to do is get back to a blank HDD download the CD version of [DBAN]("http://dban.sourceforge.net/") or go to your HDD manufacturer's website and download their utility.  They all supply programs that will wipe the drive clean.
Good luck and I hope you try Linux again soon

---

### Post by anony on 2006-10-26
> **Bartender said:**
> anony - 
Don't panic.  If all you're trying to do is get back to a blank HDD download the CD version of [DBAN]("http://dban.sourceforge.net/") or go to your HDD manufacturer's website and download their utility.  They all supply programs that will wipe the drive clean.
Good luck and I hope you try Linux again soon

I used that boot disk and fully erased the drive and windows still does not read it ](*,) 
It is an hittachi drive, where can I find such programs?
Thanks

---

### Post by anony on 2006-10-26
> **anony said:**
> I used that boot disk and fully erased the drive and windows still does not read it ](*,) 
It is an hittachi drive, where can I find such programs?
Thanks

Any ideas, anyone?

---

### Post by anony on 2006-10-27
:-k  Should I just chuck this drive? Will it ever be readable by windows?

---

### Post by anony on 2006-10-27
What if I just reinstall ubuntu then uninstall it correctly? Will that work? Although, I would prefer to completely delete everything  and restore it back to normal. Is this possible?

---

### Post by Cynical on 2006-10-27
Go [here](http://www.hitachigst.com/hdd/support/download.htm) and download the drive fitness test utility. Do a low level format.

---

### Post by dannemil on 2006-10-27
Skip all of that. Install VMWare Server, install windows as the guest in the vmware server, and run windows from within VMWare. You can share directories between the ubuntu host and the windows guest. No need to dual boot.

---

