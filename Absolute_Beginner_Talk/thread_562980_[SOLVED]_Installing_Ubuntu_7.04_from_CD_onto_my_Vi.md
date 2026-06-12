---
title: "[SOLVED] Installing Ubuntu 7.04 from CD onto my Vista PC. Help Please."
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by DavidLive on 2007-09-29
I have an Ubuntu CD, as received from LaunchPad/Canonical. I am wanting to install it onto my home PC, of which many users use.

I have never made partition, shrunk size, etc. so I am an absolute beginner.

I am going to use the Windows Disk Manager, but don't want to do anything wrong. 

I still will mostly use Vista, as Ubuntu is only for some things. Can you please help. My PC specs are below.


167.23 GB Free.
Vista Installed and used everyday.
Several Users.
Data Backed Up (Music/Pics/Videos on MP3 etc.)

Ubuntu 7.04 / Vista Desired on Launch of PC. Vista cannot be affected.
[URL="http://img235.imageshack.us/img235/2586/49916103et1.jpg"]
http://img235.imageshack.us/img235/2586/49916103et1.jpg[/URL]

---

### Post by por100pre1 on 2007-09-29
Simple, use Vista's Disk Manager to shrink HDD (Disk C). Then install Ubuntu using the Guided - use largest free space option. Just before installing, at step seven, click Advanced and select to install GRUB in hd(0,2). Finally login into Windows (Ubuntu will appear missing) and use EasyBCD to add Ubuntu to Vista's Bootloader. Hope it helps. :)

EDIT: BTW, this method doesn't replace Vista's bootloader, you can remove Ubuntu's partitions from HDD and remove Ubuntu's entry with EasyBCD if you don't like Ubuntu. You may need to use Disk Defragmenter, and Disk Cleanup before shrinking HDD Local Disk C. Give at least 30G to Ubuntu.

---

