---
title: "Fat32 partition to share files not working so good"
date: 2007-04-14
forum: Apple PPC Users
---

### Post by SpazTheCat on 2007-04-14
Hi,

Today I installed Ubuntu 7.04 beta on my Powerbook G4 (dual boot). When I partitioned using the Ubuntu installer, I created a 4GB Fat32 partition to share files between MacOS X and Ubuntu. The partition seems to be available when I boot into Linux but when I boot into MacOS X, it doesn't mount and I can't seem to make it mount. Also, when viewing my hard drive in Disk Utility, it thinks my Fat32 partition is an Apple Unix partition.

Any suggestions for fixing things so it is available to both OS's?

Thanks,

Andy

---

### Post by grazie on 2007-04-15
Firstly, FAT32 isn't a great file system and normally has a maximum partition size limitation of 2G iirc. Alternatively, use Ext2/3, HFS or HFS+ with journaling turned off for those file systems that support it.

---

### Post by SpazTheCat on 2007-04-15
Thanks for the reply but I ended up figuring it out. MacOS X will automatically recognize and mount a DOS partition if and only if the partition type is exactly "DOS_FAT_32". Ubuntu didn't correctly do this when it formatted the partition.

I am aware that FAT isn't ideal but it is the only file system that has good support in both OS's. In my experience, HFS and HFS+ are not reliable in Linux. I've had much better luck with FAT partitions. I thought the file size limit of FAT32 was 4 GB with a max volume size of a couple of TB (depending on the OS). FAT16 is 2GB for files and 4 GB for volumes (depending on OS).

Andy

---

### Post by cornish on 2007-04-16
You say that you sorted this how?

I am dual booting linux and windows and I have a partition which I want to access from both OS 

Windows E:\ 4Gb Fat 32

In ubuntu I can use the command mount /dev/hda5 /mnt/winlin this works fine but I want to know how to do this on startup 

Can you post what you done to sort your out?

---

### Post by ssam on 2007-04-16
> **cornish said:**
> You say that you sorted this how?

I am dual booting linux and windows and I have a partition which I want to access from both OS 

Windows E:\ 4Gb Fat 32

In ubuntu I can use the command mount /dev/hda5 /mnt/winlin this works fine but I want to know how to do this on startup 

Can you post what you done to sort your out?

I think feisty lets you mount internal partitions in the same ways as it does removable disks. ie they show in the side bar in nautilus, so you can just click on them.

until then you will need to add the device to you /etc/fstab see [Mounting Windows Partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

===
its FAT16 that can only handle 4GB partitions
[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by stmiller on 2007-04-16
The current kernel can read/write native OS X's file format (HFS+). No need to make a different partition!! Just mount your OS X partition and go. Also there is a project that let's you mount ext partitions in OS X. It's on sourceforge...

---

### Post by walter_f on 2007-04-18
> **SpazTheCat said:**
> Hi,

Today I installed Ubuntu 7.04 beta on my Powerbook G4 (dual boot). When I partitioned using the Ubuntu installer, I created a 4GB Fat32 partition to share files between MacOS X and Ubuntu. The partition seems to be available when I boot into Linux but when I boot into MacOS X, it doesn't mount and I can't seem to make it mount. Also, when viewing my hard drive in Disk Utility, it thinks my Fat32 partition is an Apple Unix partition.

Any suggestions for fixing things so it is available to both OS's?

Thanks,

Andy

You might try ext2fsx in order to get Mac OS X a bit more educated:

An implementation of the Ext2 (Linux) filesystem for Mac OS X.
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

Regards,

Walter.

---

