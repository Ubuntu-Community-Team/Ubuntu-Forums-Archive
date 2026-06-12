---
title: "Noob dual boot ntfs / fat32 partioning question"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Delawaredave on 2008-01-06
Had old desktop - dog under Windoze - put Xbuntu on it (with help from this group) - works great !  Single boot.

Now I have another computer that's a dog under Windows and I'd like to dual boot with Ubuntu / Windows.

However... I don't understand partioning and NTFS/FAT32 stuff.  I searched and read below link - but over my head...
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

Here's my config:  
c:  FAT32  15 G total, 4 free
d: NTFS 40 G, 27 free
g: FAT32 115 g, 40 free

I think C and D are same physical drive with two partitions.

I'd like to use the repartioning with the Ubuntu installer - appreciate any recommendations how to confugure. 

Thanks !!!

---

### Post by forestpixie on 2008-01-06
try having a look at the psychocat pages - this is about planning - but the whole shebang should be useful to you - there's a bit on installing a dual boot as well

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by erfahren on 2008-01-06
which partition (on which drive) did you want to install Ubuntu on? NTFS and FAT32 are just filesystem types used by Windows (Linux uses ext3) - with FAT32 being the older type. Linux has native read/write support to FAT32).

Basically you just need to resize a parition (somewhere) and install Ubuntu - the install will reformat it to ext3 for Linux.

Maybe you're thinking it's more complicated than it is.

This site is about installing using the AlternateCD, but much of the information is still applicable.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

He goes into partition rules (you can only have 4 primary -or- 3 primary and one extended).

He also goes into installing GRUB (which gets installed by default using the LiveCD)

resize that G: to leave about 20 GB (or more) for ubuntu - so for example:
G: 90GB FAT32 (after shrinking)

--- out of the free space create an extended partition with ---
 Linux ext3 - 24GB (mount as root "/" )
 swap - 1GB

---- OR ------

 Linux ext3 - 5GB (mount as root "/" )
 Linux ext3 - 19GB (mount as /home)
 swap - 1GB

---

### Post by 720iD on 2008-01-06
for simplicity i would recommend moving the data from your 40g drive to the spare room on your 115g drive.
partition your 40g drive with swap and root partition and install, you can add home and other partitions later when you become more familiar with the system.

this repartitioning can be done simply with the installer on the live cd

---

### Post by 720iD on 2008-01-06
as an after thought if you do use the 40g just point the installer to the drive and use guided partitioning. all the partitioning will be done for you.

---

### Post by Delawaredave on 2008-01-08
> **720iD said:**
> as an after thought if you do use the 40g just point the installer to the drive and use guided partitioning. all the partitioning will be done for you.

Thanks for your help.   I clicked the installer and started through some screens - then I got "scared" that it was going to overwrite my Windows OS.

Does it ask you for "dual boot" ? Or does it automatically keep existing Windows on there ?

When I "point the installer to the 40 G partition" - will it not disturb the Windows stuff there ?

Sorry for simple questions.  Thanks !

---

### Post by erfahren on 2008-01-08
go with the "manual option" for the partitioning - that way you can see exactly what you are doing (it isn't hard)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Delawaredave on 2008-01-08
Thanks for everyone's help - I am dual booting with Ubuntu !

I don't quite understand where/why/how the install put the partitions - but Windoze is still there and intact.

Bunch of other stuff I've got to learn on Ubuntu....

Thanks for your help !

---

