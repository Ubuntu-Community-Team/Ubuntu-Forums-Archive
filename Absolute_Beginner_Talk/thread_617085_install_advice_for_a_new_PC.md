---
title: "install advice for a new PC"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Yellowdog428 on 2007-11-19
I am building a new system and need some install advice.

Like many out there I have fallen for Ubuntu, but I still need Windows for school/work, so I am trying to figure the best install method.

I am going to run two 250 Gig SATA drives and planning to run Ubuntu as my primary OS.  I was thinking I would partition the first drive 100-150 Gig for Ubuntu, 50-100 Gig for Windows and leave the rest on that drive unpartitioned.  (I also have a Vista Disk I may want to play with later)

Then Format the next drive as FAT to save docs/music/video accessible by both OS.  

Is this the best setup in your opinion?  If not what would you do?

Also I have been playing with VMWare but haven't been able to figure how to boot a native OS from it (Instead of creating a new install, is it possible?)

Thanks guys for your help and feedback!

Cheers

---

### Post by MegaJim on 2007-11-19
I would say 100-150GB is way too much for ubuntu, it really only needs 10G, 20G if you are going to download LOADS of stuff from other repositories...

To keep things simple I would use the whole of one disk as a 250gb NTFS shared data partition where you can freely read/write data from both Windows and Linux, it also has the advantage of being easy to restore data if the partition tables should be damaged.

As for the system setup I would recommend having the windows OS on its own primary partition at the start of the first disk and make it as large as it needs (on my setup I just give XP 25gigs and use a seperate partition for games but w/e).

I like to have a small 150mb /boot partition in reiser format which can store your bootloader and config (so swapping OS is easier and your system is more fault tolerant), These next partitions are inside a logical partition - then make partitions for / (root- 10-20gb) and /home (as your data is going to be on the 250g drive, this can be small enough for general config files, say 5gb) and finally the linux swap at the very end of the drive in its own primary partition.

So its like this...

(Primary partition)Windows | (Primary partition) /boot in reiser 150mb | (Extended partition) (Logical partition) / Root 10-20GB | (Logical partition) /home 5gb | (Primary partition) Linux Swap size is 2x RAM

---

### Post by Yellowdog428 on 2007-11-19
great!  That is what I was looking for.  

But you are saying that NTFS is a good format for my data drive and not FAT??  I thought I heard that FAT is a better format for storing data for Linux/Windows to read and write to, I could be delirious tho...

Cheers

---

### Post by cmnorton on 2007-11-19
> **Yellowdog428 said:**
> great!  That is what I was looking for.  

But you are saying that NTFS is a good format for my data drive and not FAT??  I thought I heard that FAT is a better format for storing data for Linux/Windows to read and write to, I could be delirious tho...

Cheers

Given ntfs is a journaling file system, you're buying more data integrity if the system goes down, and Windows doesn't read ext2/3.

---

### Post by rsambuca on 2007-11-19
For your data/media drive, I would use either ntfs or ext3, depending on what system you use most.  If you use linux most, then make the drive ext3, and use the fs-drivers for Windows for full read/write access.  If you use Windows most, then make the data drive ntfs and Ubuntu can read/write to it with the ntfs-3g drivers (default in Gutsy).

FAT32 is basically a terrible filesystem that you really don't need for hard drives anymore.

---

### Post by mike555 on 2007-11-19
Keep in mind if you give Windows full access to your extra partition , and if you get a virus it might mess up all your stuff in there ......

---

### Post by MegaJim on 2007-11-19
yeah, and if you download a shellscript from somewhere you don't trust and run it on linux you could delete everything on all your hard drives.  Idiots are idiots, this guy obviously knows what he is about, give him some credit ;)

---

### Post by rsambuca on 2007-11-19
> **mike555 said:**
> Keep in mind if you give Windows full access to your extra partition , and if you get a virus it might mess up all your stuff in there ......

Generally Windows viruses don't just "mess up stuff" on data drives.  Today's viruses tend to hide themselves in system files, registries, etc.

---

