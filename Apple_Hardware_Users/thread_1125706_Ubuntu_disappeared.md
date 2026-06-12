---
title: "Ubuntu disappeared"
date: 2009-04-14
forum: Apple Hardware Users
---

### Post by janus12 on 2009-04-14
Alright, so the situation is this. I had a Ubuntu/OSX (8.10 64/10.5) dual boot on my MacBook (4,1) using rEFIt. It was working fine. The problem was that there was no way to transfer files from the Ubuntu side to the OSX side. I think pretty much everyone has this problem, since OSX can't read ext3 and Ubuntu can't write to journaled HFS+.

So, I got the idea to create a small HFS (not HFS+) partition using gparted, which was about 2 gigs. I had extra space on the HD, so I didn't touch any of the existing partitions at all. I drop a file in there, reboot to OSX, and everything works fine. Both OSX and Ubuntu have read/write access.

Except rEFIt no longer recognizes the Ubuntu at all. At first I assumed it was just a partition table syncing issue, but nope. I've tried running the partition tool in rEFIt, re-installing rEFIt, and deleting the HFS transport partition, with no luck. Here's the report from rEFIt:


```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    411462535  Mac OS X HFS+
 3      411462536    412048473  Basic Data
 4      412048474    452831677  Basic Data
 5      452832136    456928135  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    411462535  af  Mac OS X HFS+
 3 *    411462536    412048473  83  Linux
 4      412048474    452831677  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 411462536:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 412048474:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 452832136:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type MS Reserved
```

If it's not obvious, 2 is the OSX, 3 is the boot, 4 is the Linux filesystem, and 5 is the Linux swap. This is after I deleted the HFS partition. I'm thinking it has to do with the * on the Linux boot partition, but I don't know what * means. I don't know how creating a new partition from existing free space could possibly screw up the existing partitions, but there it is.

Anyways, I guess there's really two possibilities: either I can save it or not. I'm hopeful that I can save it, since I didn't alter the Linux partitions at all, AFAIK. If I can, I'd think it would be a simple fix? Hopefully.

If I can't save it, then I have another question. I didn't back up before doing this (smart), and there's a few files on the Ubuntu side I'd like to save. Size is no issue, less than 2GB total. I have no problem reading the partition from a live CD, except I don't have read permissions from the CD. How would I save these, if possible? Of course, I'd only be deleting/reinstalling on the boot partition, but I'd need the correct permissions on the new Ubuntu install.

Even better, if someone could tell me what went wrong and how to avoid it, I'd be forever in your debt. Others too, since having a "transfer" partition seems like good solution to the problem of file transfer, without having to disable journaling and mac permissions.

Thanks for the help.

---

### Post by cyberdork33 on 2009-04-14
> **janus12 said:**
> Except rEFIt no longer recognizes the Ubuntu at all. At first I assumed it was just a partition table syncing issue, but nope.
Did you try reinstalling grub?
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

> **janus12 said:**
> This is after I deleted the HFS partition. I'm thinking it has to do with the * on the Linux boot partition, but I don't know what * means. I don't know how creating a new partition from existing free space could possibly screw up the existing partitions, but there it is.

The * marks the partition that is flagged as bootable. I wouldn't worry about that.

I did notice that your swap partition is recognized as "type MS Reserved" which it should not be. I am not sure that it is causing your issue though.

> **janus12 said:**
> Anyways, I guess there's really two possibilities: either I can save it or not. I'm hopeful that I can save it, since I didn't alter the Linux partitions at all, AFAIK. If I can, I'd think it would be a simple fix? Hopefully. I think you can save it since all the files are accessible :)

> **janus12 said:**
> I have no problem reading the partition from a live CD, except I don't have read permissions from the CD. How would I save these, if possible? Of course, I'd only be deleting/reinstalling on the boot partition, but I'd need the correct permissions on the new Ubuntu install.
Those files belong to a different user than the LiveCD user, thus the LiveCD user does not have permission to act on those files. You can open a file browser with root permissions (gksudo nautilus) and then you should be able to access the files. You can also chmod the files to edit the permissions on the files.

> **janus12 said:**
> Even better, if someone could tell me what went wrong and how to avoid it, I'd be forever in your debt. Others too, since having a "transfer" partition seems like good solution to the problem of file transfer, without having to disable journaling and mac permissions.
For a shared partition, FAT32 is your best bet. The only time that you would not want this is if you plan to put a single file that is larger then 4GB on the partition.

---

### Post by janus12 on 2009-04-17
Ha! Thank you. Reinstalling Grub did the trick.

Is this a known bug?

---

### Post by cyberdork33 on 2009-04-17
> **janus12 said:**
> Ha! Thank you. Reinstalling Grub did the trick.

Is this a known bug?
the same bug that causes the partition tables to be out of sync sometimes messes up grub as well. I believe this bug is finally fixed in Jaunty though (fix should be on the RC that was released yesterday).

---

