---
title: "Help straighten me out on adding partitions..."
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Permanent Beginner on 2007-07-27
When I installed Ubuntu, basically by pushing every button that said "go ahead", I ended up with a drive that looks like this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 65 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device         Boot          Start          End               Blocks      ID      System
/dev/sda1     *                    1        19175       154023156    83       System
/dev/sda2                      19176     19457       2265165         5         Extended
/dev/sda5                      18176      19457       2265133+     82        Linux swap / Solaris

Now I've been spending the last couple of hours searching the Web for some more information of all of this, with no success, so may I humbly trouble the community again?

Question #1:  I can kinda guess that all that heads and cylinders stuff pertains to the physical configuration of the media in the drive.  What is a block?  What is a unit?  How do I read the sector size from these numbers?

Question #2:  It seems kind of primitive that almost the whole thing is in one partition.  This machine is intended to be nothing but one big tape recorder, and I think it ought to have a separate bag containing the music files so the system doesn't have to paw through them all when it's looking for something.  Instructions for adding a partition are surprisingly hard to find.  I did run across Gparted, which looks like what I want, but it assumes that the user knows what "kind" of files these are.  I'm guessing NTFS.  Is this at least a good enough guess to go with?

Question #3:  Where are sda3 and sda4?

Question #4:  I've seen many partition list displays in sites and books, and all the partitions are /something, like /sda1 or /tmp or /usr.  Presuming that these terms have some sort of meaning, what should be the denomination of my bag of music files?  /usr maybe?  Can I just dream up a suffix or is there a list of things it has to be?

Thank you kindly.

PB

---

### Post by FleetAdmiral74 on 2007-07-27
To question 4

Your music files (along with everything else thats yours) should normally go in /home

So you should have a / partition, the /swap, and /home where all your stuff goes. the / is for the OS. A quick google of making new home partition in ubuntu will show you the proper guides. 

When I say you should...right now your /home is just part of the /. The point of making it seperate means you can upgrade your OS to anything (the /) and not touch /home, where as if its integrated in / it would be deleted on a format.

hope thats clear...i'm really tired

edit: I don't quite get question two when you talk about different kind of files...do you mean file systems, like ext3 and FAT32? Or like .odf and .ogg

---

### Post by mikewhatever on 2007-07-27
1. Generally, a good source of information for Ubuntu is help.ubuntu.com. Try the following link for fstab [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

2. There is only one partition, I guess, to keep things simple. You are free to create more if needed.

3. No idea.

4. It is better to dream up a meaningful word, such as /music. Do not use /usr, because that's one of the system directories.

---

### Post by AceofSpades19 on 2007-07-27
/tmp  and /usr for example are mountpoints, thats where you access a drive. sda1, sda2 are the actual paritions

---

### Post by Permanent Beginner on 2007-07-27
.
"I don't quite get question two when you talk about different kind of files...do you mean file systems, like ext3 and FAT32? Or like .odf and .ogg"

Oh, I'm sorry, I used the wrong word.
Gparted says it can work on ext2,ext3,fat16,fat32,hfs,linux-swap,ntfs filesystems.  If the filesystems that Ubuntu created are one of these I guess it'll work, but I don't know how to find out.
.

"/tmp and /usr for example are mountpoints, thats where you access a drive. sda1, sda2 are the actual paritions"

Ooh, that's hot info.  Thanks!

PB

---

### Post by az on 2007-07-27
> **Permanent Beginner said:**
> 
Question #1:  I can kinda guess that all that heads and cylinders stuff pertains to the physical configuration of the media in the drive.  What is a block?  What is a unit?  How do I read the sector size from these numbers?

I dunno.  You don't really need to know this sort of under-the-hood stuff to partition your drive.

> **Permanent Beginner said:**
> 
Question #2:  It seems kind of primitive that almost the whole thing is in one partition.  This machine is intended to be nothing but one big tape recorder, and I think it ought to have a separate bag containing the music files so the system doesn't have to paw through them all when it's looking for something.  Instructions for adding a partition are surprisingly hard to find.  I did run across Gparted, which looks like what I want, but it assumes that the user knows what "kind" of files these are.  I'm guessing NTFS.  Is this at least a good enough guess to go with?

All-on-one partition is the safest and easiest way to go.  Unless you have special needs, there is no need to partition your drive.  An example of a special need is a mail server which can get shut down if the hard drive fills up.  You used to be able to take down a mail server by overloading the system logs with useless messages.  If the logs are kept on a separate partition, that partition fills up and then that's it.  The system keeps ticking on.

Now, if you created a separate home partition, you run the risk of making your root partition too small.  Them you would be stuck.  There is no advantage to a separate root partition these days.  In the olde days of unix, when hard drives were expensive it may have been a better option for a workstation...  It's no longer needed.

So, all-on-one partition works just fine.  You can still mount other drives or partitions and store your stuff there.   That's your choice, but it's not a must for a default install.


> **Permanent Beginner said:**
> 
Question #3:  Where are sda3 and sda4?

sda could be the first SATA drive or the first IDE drive.  IDE drives used to be called hd, but the kernel driver for sd will accommodate both Sata and IDE.  sda3 is the third partition on the first drive.  sdb1 would be the first partition on the second hard disk.  I say hard disk, but it can be any device, like a cdrom...

> **Permanent Beginner said:**
> 
Can I just dream up a suffix or is there a list of things it has to be?


Yes and no.  You can mount anything you want anywhere you want.  The trouble is, if something else is using that mountpoint, you will screw up your system.  For the sake of standards-compliance (look up linux filesystem hierarchy)  you mount removable devices in /media.  (ex: /media/usbdrive)  I happen to have a few extra hard disks mounted as /store and /backup, but they probably would be better somewhere else (like /mnt/store and /mnt/backup).  But that's just messy me.

---

