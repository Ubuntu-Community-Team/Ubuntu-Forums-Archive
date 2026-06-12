---
title: "TrueCrypt dual boots"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by TopHatCat on 2007-03-23
On a single HDD I am installing Windows XP Professional on one partition, Ubuntu 6.10 Edgy on a second partition, and using a third partition as storage space encrypted with TrueCrypt.

**My question is**: Does anyone have experience using TrueCrypt with Linux and assuming that this third volume is FAT32 will both my XP and Ubuntu partitions be able to access files in that storage area?

Does Linux recognize NTFS?

---

### Post by chewearn on 2007-03-24
> **TopHatCat said:**
> On a single HDD I am installing Windows XP Professional on one partition, Ubuntu 6.10 Edgy on a second partition, and using a third partition as storage space encrypted with TrueCrypt.

**My question is**: Does anyone have experience using TrueCrypt with Linux and assuming that this third volume is FAT32 will both my XP and Ubuntu partitions be able to access files in that storage area?
I have a similar setup.  I use a external harddisk with a single truecrypt encrypted partition.  No problem to get it to work, though the linux version truecrypt is command line only.

Some pointers:
1. use windows to create the partition; the gui makes it much more intuitive.  Plus, I have not figured out how to use linux to format the "base" filesystem to other than ext3.  Base means the outside area where the encrypted resides.

2. in linux, you have to use e.g. /dev/hda3 to refer to the encrypted partition.  In the manual, they only mentioned "encryptedfile.tc" in the examples, which basically means encrypted file (as opposed to partition).

3. If you use external (usb) drive, you can use sudo fdisk -l to discover the partitions info; this tells you whether to the drive is /dev/sda1 or /dev/sdb1, etc.

> Does Linux recognize NTFS?
Logically, NTFS should work, but I have not done this.
In my setup, the base partition is reported as FAT16 in linux, and unknown/unformatted in windows xp, but the encrypted partition is FAT32.

Update:
I look into this thread (it has a script for linux gui mount) it appeared there is a new gui for truecrypt:
[http://ubuntuforums.org/showthread.php?t=380469](http://ubuntuforums.org/showthread.php?t=380469)

---

