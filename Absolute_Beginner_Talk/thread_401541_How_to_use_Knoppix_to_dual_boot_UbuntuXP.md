---
title: "How to use Knoppix to dual boot Ubuntu/XP"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-04
Is it possible to use Knoppix to take a portion of my existing HDA1 partition, which Ubuntu is installed on, say 20 GB, and install windows on it? So that I can play games at full speed without needing to use Cedega or WINE?

---

### Post by cypherzero on 2007-04-04
Do you mean use Knoppix to partition your hard drive and then install Windows to the new partition?
If so why not just use GParted in Ubuntu?
As a warning though windows may (should!) overwrite the MBR with NTLDR and you will have to reinstall GRUB, which may prove tricky.

---

### Post by LaurelLynn on 2007-04-04
Dear Peter1234123,

I have used Knoppix to go the other way (resize an NTFS partition to make room for Knoppix).

QTParted has a Resize Partition option that works with many filesystems. The trick is it will refuse to squash over existing files, so the disk has to be defragmented first (a useful safety feature). Even then I found that the windows defrag insisted on leaving files in the middle of the partition).

I´m embarassed to admit it but I don´t actualy know how to defrag a Linux partion. Try Google ¨Linux defrag¨.

Note: Unless you backup the partition (say to an external USB drive), you run the risk of loosing everything.

At the very least backup the boot sector from the MBR before you start, Windows will write over it and erase Grub. Assuming your drive is HDA:

dd if=/dev/hda  of =¨someplace safe¨ bs=512 count=1

After the install you have to either change the windows bootloader to include an Ubuntu option, or restore the Grub bootloader by:

dd if =¨someplace safe¨ of=/dev/hda  bs=446 count=1 (note: 512 would restore the old partitions)

At which point Ubuntu would now boot but not windows.

 Googling ¨grub windows boot¨ should locate instructions on adding the new windows install to grub.

Laurel Lynn

---

