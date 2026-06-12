---
title: "Partitioning Question #1000001 :D"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by AliL on 2007-09-27
Right then, sorry to add another post to the forums about partitioning, but I'd like to get a definitive solution on the issue and then make a wiki page out of it...

As with many users I want to dual boot into Windows/XP and be able to access my files (music, video, documents etc.) from both.

This means that i want several partitions:
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]1 for Windows/XP,[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]1 for Ubuntu,[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]1 for my files,[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]and 1 for my swapfile.[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Obviously I'll need to install windows first, and I'll give this 15GB (I have a 120GB HDD).

Here's where I need the help:
1. Should I give the / directory about 15GB for the main files (like XP has), and then the /home directory the rest?
2. What file format should I give the /home directory - FAT32, NTFS, ext2 or ext3?
3. Will I need a /boot directory?
4. In XP I want to move the My Documents folder to a separate partition, which is easily enough done, but can this be the same partition as the /home directory in Ubuntu or will there be conflicts? For example directories starting with a period (.). Could these just be hidden in windows explorer or would it cause conflicts in Ubuntu?

_Extra curricular questions :P_

5. What is a journalling file system (I know ext3 is an example but what does it DO)?
6. Why does Ubuntu recognise my HDD as sda when it is an IDE drive? I thought IDE drives were recognised as hda?
7. What is the difference between primary, logical and extended filesystems?

I hope this isn't too much to ask, but it could help so many users in the future if I got these answered...

---

### Post by logos34 on 2007-09-27
You might want to take a look at this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I'd create a primary partition for windows C: , and then make an extended partition on the remaining disk space and put everything else inside: D: My Documents, 10GB linux root, 1GB swap and rest ext3 /home.  You don't need a separate /boot.  Get fs-driver so windows can r+w to ext2/3 and ntfs-3g for linux.

[http://tldp.org/HOWTO/Partition/partition-types.html](http://tldp.org/HOWTO/Partition/partition-types.html)
[https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks)

---

### Post by AliL on 2007-09-27
Shame I didn't mention that I'd seen the psychocats pages before and found them less than useful...

But thanks for the launchpad page, I'm not totally sure but I'm guessing it means that the libata module is treating my discs as SATA drives, but does this mean that it is now limited to 15 logical partitions instead of 63?

Also, are you suggesting that I have a seperate partition for "My Documents" and "/home"?

Why put the swap file in the extended partition? Surely it would be better to put it on its own primary partition as your tldp.org page says that I have to have the partitons in a contiguous order so it would be stuck in the middle?

---

### Post by logos34 on 2007-09-27
> **AliL said:**
> But thanks for the launchpad page, I'm not totally sure but I'm guessing it means that the libata module is treating my discs as SATA drives, but does this mean that it is now limited to 15 logical partitions instead of 63?

no, 63 is the limit (a sata drive is serial ata, not scsi, even if the libata driver sees them alike).
> 
Also, are you suggesting that I have a seperate partition for "My Documents" and "/home"?

Yes, you'll have to unless you use fs-driver from windows side (your /home really should be ext3).

> Why put the swap file in the extended partition? Surely it would be better to put it on its own primary partition as your tldp.org page says that I have to have the partitons in a contiguous order so it would be stuck in the middle?

Swap can be a logical or primary, doesn't matter.  The ubuntu guided partitioning option will actually create swap as a logical partition.  It's just easier (IMO) to create your windows system partition and throw everything else into an extended--make the swap first then the rest. 

There is a third option: a [shared fat32 data partition]("http://users.bigpond.net.au/hermanzone/p2.htm").  But vfat has a max. 4 GB file size limit, it fragments more easily and is an inferior filesystem.

---

### Post by AliL on 2007-10-02
OK, so I've installed Ubuntu on a primary partition 15GB in size, the swap on another 2GB in size, and /home on the last primary partiton taking up the rest of the space.

The / and /home partitions are both ext3, and the /home partition is being accessed through Windows XP using the fs-driver, and is being doubled up as the folder for "My Documents" as well.

However I've found a problem or two. During the transfer of the files on XP, the desktop.ini files became unhidden and un-systemfiles.

1. How do I get these attributes back?

2.Also, on Ubuntu, the My Pictures/Music/Videos folders only have have root permissions and not user permissions, how do I change these back to default?



Edit: I got the permissions of the My Pictures etc. folders to how the other folders were in the /home folder (i.e. alil (my username) has access) by opening up a console and typing: ```
 sudo nautilus 
``` ...and changing the permissions manually.

---

