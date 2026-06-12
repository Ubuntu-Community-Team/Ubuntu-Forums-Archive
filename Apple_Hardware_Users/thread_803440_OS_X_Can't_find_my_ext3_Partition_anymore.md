---
title: "OS X Can't find my ext3 Partition anymore"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by russo.mic on 2008-05-22
So,  As of a 8.04 install of kubuntu, OS X No Longer finds my ext3 partition.  I've got the driver installed in OS X, but a diskutil list in OSX shows this:

#:                   type name               size      identifier
   0:  GUID_partition_scheme                    *111.8 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS OS X               12.8 GB   disk0s2
   3:                    EFI                    78.4 GB   disk0s3
   4:   Microsoft Basic Data Untitled           20.4 GB   disk0s4

Can't think that it's normal for the ext3 partition (3rd partition, 78 Gigs) to be listed as EFI...what gives?

Thanks in advance!

Russo

---

### Post by cyberdork33 on 2008-05-22
> **russo.mic said:**
> So,  As of a 8.04 install of kubuntu, OS X No Longer finds my ext3 partition.  I've got the driver installed in OS X, but a diskutil list in OSX shows this:

#:                   type name               size      identifier
   0:  GUID_partition_scheme                    *111.8 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS OS X               12.8 GB   disk0s2
   3:                    EFI                    78.4 GB   disk0s3
   4:   Microsoft Basic Data Untitled           20.4 GB   disk0s4

Can't think that it's normal for the ext3 partition (3rd partition, 78 Gigs) to be listed as EFI...what gives?

Thanks in advance!

Russo

What does the refit partition tool report? (this is in your utilities folder as well).

---

### Post by russo.mic on 2008-05-22
The Partition Inspector?  says the following:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     27148327  Mac OS X HFS+
 3       27148328    191658093  EFI System (FAT)
 4      191658094    234436544  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     27148327  af  Mac OS X HFS+
 3 *     27148328    191658093  83  Linux
 4      191658094    234436544  07  NTFS/HPFS

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

Partition at LBA 27148328:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 191658094:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

Does this mean I just have to sync?  

Russo

---

### Post by cyberdork33 on 2008-05-23
Yea, it is set as a EFI partition in your GPT for some reason, and I think that is the problem. Maybe the GPT boot flag on your Linux partition somehow (should be on the EFI partition). IDK

I think this problem (or something similar) may apply to your situation:
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

### Post by Seaniesean on 2008-06-22
Hey, i have this problem, but it is my NTFS windows volume that comes up as "EFI" using diskutil list.  That link couldn't help i don't think, because the NTFS volume does not mount or show in the disk utility application at all, not even greyed out.  I have no trouble booting into this  windows partition with refit, however.  

I used gparted at some point in this setup, probably not very carefully at all.

Anyone fancy taking a look at my partition tables?  Pretty please?

refit partitioning tool gives this, which doesn't look right, even to me:

current GPT partition table

#             Start LBA          End LBA            Type

1                 40              409639              EFI(FAT)
2              409640            90294335            HFS+
3              90849320          156301447          EFI(FAT)

current MBR

# A            Start LBA          End LBA            Type

1                  1             409639         EE EFI Protective
2               409640          90294335        AF Mac OSX HFS+
3*              90849320        156301447       07 NTFS/HPFS

and it says, tables are synchronized, no need to sync.  Hmm.

So, can anyone see what's wrong here, and what to do about it?

Edit- Sorry, that didn't come out at all like i typed it.

---

### Post by cyberdork33 on 2008-06-23
this might help
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

### Post by pelle.k on 2009-11-09
I had this problem, after i installed fedora, and figured i would set the "boot" flag on fedora partition with parted. Big mistake.

First of all, the MBR partition table wasn't synched with the GPT partition table (probably a bug in fedora), so i couldn't use the command line "fdisk" in OS X to manage partitions (to set them as bootable and whatnot). I never have problems with the MBR synching with the GPT when using ubuntu though.
I fixed that problem with running gptsync from a terminal.

My second problem was that I tried using parted to set the fedora root as "booatble". Again, big mistake. I should have used "fdisk" in OS X as i always do. Anyway, it did set the "msftres" on that partition, making it invisible to OS X and disk utility.
I fixed that by booting linux, running gparted and set the "boot" flag (resets the msftres flag). Then i cleared the "boot" flag as well, and finally i booted OS X, and used the fdisk to set the "boot" flag instead (as i should have done from the beginning really).

Hope this helps someone.

---

