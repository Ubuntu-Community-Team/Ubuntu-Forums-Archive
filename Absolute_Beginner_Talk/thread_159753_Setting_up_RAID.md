---
title: "Setting up RAID"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by fgcolin on 2006-04-13
I have 2 SCSI drives that I would LIKE to RAID. How do I need to go about setting all that up. I've gone through the partitioning process and everything seems to NOT work. Anyone have some sort of trouble-free guide to set up 2 SCSI drives on a RAID 0 or 1. Doesnt matter which. Just tinkering and such.

---

### Post by Sandlst on 2006-04-13
Could you please describe the exact problem you are having?  Im running a Raid0 with two drives right now, maybe I can help.

---

### Post by fgcolin on 2006-04-13
Okay well heres what I've done to the best of my knowledge to try to 'get things to work'

I have 2 40 GB SCSI harddrives and I set them both up for RAID with swap files and such. I don't know if which needs to be primary or logical, if at all but I have Drive 1 set to Primary and Drive 2 set to logical. I then set up a RAID 0 so it appeard as a partition with a combined total of both harddrives (80 gig). The format was set to FAT32(any better suggestions?) with '/' for the root. I then proceeded to install the base system and it gave me an error having to do with '/target/var/log/bootstrap.log' Not quite sure what to do now.



I started typing this when I was tinkering around some more and SOMEHOW I got it to work. Weird how I got it to, this is what I did.

I deleted the RAID partitions on both the drives and left the FAT32 partition on the RAID partition and tried installing the base system. It went right through with no errors. I can't explain it but its working now. I WOULD still like it though if you could tell me how YOU did it so I can see how to do it correctly. Any better suggestions on what format to make my RAID partition? Something to get more 'bang for my buck?'



Again, another update. Now I got the error 'grub-install (hd0)' Man...this is so tedious...any more help? I know this is a boot-loader...what exactly is that?





Update: The files are supposedly on the harddrive but now it just cycles through network boot and harddrive boot and never loads to the OS. Is THAT what a boot loader does?

---

### Post by Sandlst on 2006-04-13
I know by default, using lvm requires you to create a seperate /boot partition, I assume from the errors you are having its the same.....I went straight from lvm to raid so I kept my /boot....you probobly dont want to reinstall now :P, but thats what I did to get it working with lvm....just make a small partition, less than 100mb in ext2 or 3 with the mountpoint /boot, then create the raid drives as usual, also if you get an error while loading grub and have a hardware-raid enabled in your bios, that might be the reason.  For a reason I dont quite understand (raid is quite foreign to me) grub refused to work until I removed the hardware raid setup.  Go to the fifth post down on this thread to see about different filesystems: [http://www.ubuntuforums.org/showthread.php?t=154087&highlight=filesystems]("http://www.ubuntuforums.org/showthread.php?t=154087&highlight=filesystems")

---

### Post by fgcolin on 2006-04-13
Alright, let me just make sure I am doing this all correctly and that I'm not just wasting my time. This is what my partitioning screen looks like. Am I doing this wrong? Did I not understand your directions? Please let me know.


KEY: :rolleyes: unfilled alien looking dude
        :mrgreen: filled in smile face


RAID0 device #0 - 73.3 GB Software RAID device
     #1 73.3 GB   :rolleyes:    FAT32     /
SCSI1 (0,0,0) (sda) - 36.7 GB Seagate
     #1 Primary     98.7 MB     :rolleyes:   ext3     /boot
     #5 ;pgical      36.6 GB :mrgreen: RAID
SCSI (0,1,0) (sdb) - 36.7 GB Seagate
     #5 logical      36.7 GB     :mrgreen:   RAID


Am I missing something? Is that /boot partition under the wrong device? Should it be under RAID0 instead of the first harddrive? Should certain partitions be logical instead of primary or vice versa? If anyone can elighten me on this situation, that would be greatly appreciated.

---

### Post by Sandlst on 2006-04-13
It looks fine to me, but I am by no means an expert-I would post my partition scheme, but Ive just discovered its displaying it incorrectly.....I also noticed you have no swap partition, but that wont be a problem if you have a lot of memory, if you want to add one it should be ~2x your RAM, you can just select swap under Use As: while making a new partition.

---

