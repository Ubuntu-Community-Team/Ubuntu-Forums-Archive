---
title: "is there any difference between Ext2 and Ext3"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jaya28inside on 2008-02-14
coz i found it when first installing UBUNTU

there's an option to be choosen when we're in the Partition of the HDD right?

so what's the difference any way?

coz i know
NTFS is good for a big file.. capable to handle it more better
otherwise is named the FAT32...

so for Ext3 and Ext2...?  :guitar:

---

### Post by Rocket2DMn on 2008-02-14
ext3 is essentially the ancient ext2 filesystem + journaling.  In a nutshell, it means if the drive has a rough disconnect, you won't have to fsck it each time.  NTFS is convenient for going between linux and windows, but you can get a driver to read ext2/3 in windows at [fs-driver.org]("http://fs-driver.org").  NTFS requires the ntfs-3g driver in linux which comes preinstalled in Gutsy.
FAT32 can only handle up to 4GB files but is read natively by both linux and windows.

---

### Post by dcstar on 2008-02-14
> **jaya28inside said:**
> coz i found it when first installing UBUNTU

there's an option to be choosen when we're in the Partition of the HDD right?

so what's the difference any way?

coz i know
NTFS is good for a big file.. capable to handle it more better
otherwise is named the FAT32...

so for Ext3 and Ext2...?  :guitar:

As stated, EXT3 is EXT2 with Journaling. Journaling makes any file system more reliable (less chance of you having corrupted/lost data), but there is a performance cost in using the journal and the journal itself takes up disk space.

There are command line tools for converting EXT2 to EXT3 and vice-versa, so you are not "locked" into either one.

EXT3 is a good, solid file system that is the right choice for most Ubuntu users - there are others that have various different attributes that can be more suitable depending on the circumstances of use.

If you need a Windows compatible file system for interchanging data, then have a separate NTFS partition somewhere.

---

### Post by jaya28inside on 2008-02-22
because now is using Ext3
seems like the HDD is become slowly... 

actually my HDD is 30 GB
so i devide them into 2 Drives:

1) into Ext3 as 9 GB
2) into Swap as 1 GB

so then looks like become more slower...and i'm still having the Blank screen
problems...sigh... :(

---

### Post by philinux on 2008-02-22
Open a terminal and run 

top

See if anything is eating resources. Could be trackerd.

---

### Post by jaya28inside on 2008-02-22
OK then i'll try for it

but looks like it's the  HDD probs
coz the RED LAMP 
giving a sign of accessing files..is too hard...

---

