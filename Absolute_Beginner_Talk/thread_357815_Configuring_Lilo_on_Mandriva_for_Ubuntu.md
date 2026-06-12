---
title: "Configuring Lilo on Mandriva for Ubuntu"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by spenny on 2007-02-10
:guitar: 
I have PC which had Windows on the first hard drive and Ubuntu on the second hard drive. I downloaded Mandriva and, feeling very gung-ho, did an install deleting the Windows installation. 

Now when I get the boot loader (Lilo), my option to boot up Ubuntu from the second hard drive has disappeared. 

How can I configure it (preferably from within Mandriva) so that I get the Ubuntu option in the boot list?

The partitions I have are as follows:

1st HD (hda):
hda1 mountpoint: / journalised FS: ext3
hda5 mountpoint: swap
hda6 mountpoint: /home journalised FS:ext3

2nd HD (hdb):
hdb1 NTFS (this is a windows partitioned drive for a back up of my windows stuff)
hdb2 journalised FS:ext3
hdb5 swap

Thanks in advance,
Andrew.

---

### Post by spenny on 2007-02-10
OK, never mind. I've worked out how to do it. I changed the configuration to load from Grub, booted from a Knoppix Live CD, copied the Ubuntu entries from menu.lst to the menu.lst on the Mandriva partition and all was well.

---

