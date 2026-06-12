---
title: "Newbie Dual Boot Question"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by todd1049 on 2007-12-20
I am planning on getting a new computer and I want to set it for dual boot with Windows (Vista) and Ubuntu.  What is the best way to partition the drive?  Should I use FDISK (or whatever the MS utility for partitions is these days) and create a small partition for the boot sector, followed by larger partitions for windows and linux?  Also -- if I have data that I want both Windows and Ubuntu to be able to access -- should I create another partition for that?  I have not used GRUB at all yet, but would be open to suggestions if folks believe that to be a more efficient solution.  Many thanks for the help!

---

### Post by Severun on 2007-12-20
Just install Vista first and tell it to take half of your disk.

Then Install Ubuntu second and tell it to use the unused disk space.

As far as accessing files by both.  use ntfs-3g (allows read/write of Windows filesystems from Linux).  You can install it from Synaptic package manager if it doesn't get installed by default.

You don't have to worry about boot sector, as when you install Ubuntu it will take care of installing grub which will let you choose between booting vista or Ubuntu.

---

### Post by erfahren on 2007-12-20
this site has a lot of good information about general dual booting, GRUB, etc.: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
- it's mainly about using the AlternateCD (text based installer) but it has very comprehensive information about other things that are still applicable.

At on time it was a good idea to have a partition (formatted to FAT32) for both OSs to share but I think Gutsy has native read/write support for NTFS now. 

there's also this guide specifically about dual booting with Vista: [http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)
I didn't have any problems with GRUB picking up on my Vista and adding it to the /boot/grub/menu.lst but you need to pay attention to what it says about not using the Ubuntu partitioner to resize the Vista partition.

(If the PC already has a seperate data (D:\) partition you'd be in business, you could just use the Windows Disk Manager (part of the Administrative Tools) to resize that partition for Linux.)

GRUB gets installed by default (although you can select for it not to be). It's pretty easy to configure once you're in Ubuntu. That first guide I linked to goes into all of that.

Another good guide (for the LiveCD) here: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

