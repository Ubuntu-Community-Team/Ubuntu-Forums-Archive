---
title: "MacBook Pro GRUB  Install Problem"
date: 2010-08-04
forum: Apple Hardware Users
---

### Post by simeon.fm on 2010-08-04
I just got a refurbished MacBookPro5,1 and I want to dual-boot Mac OS 10.6 and Ubuntu 10.04.

So far, I've followed all of the steps in the general MacTel installation wiki up to running the Ubuntu installer from the LiveCD: I made a BootCamp partition, installed rEFIt, booted from the LiveCD and deleted the BootCamp partition with Gparted. 

I've run through the 10.04 installer to the last step where, in the wiki, it says to select "Advanced" and install grub to /dev/sda3. 

Here's where my troubles are. 
When I select "Use largest continuous free space" earlier in the process, I'm only shown sda (the whole drive), sda1 (EFI partition), sda2 (OS X) and two instances of sda-1(?). 
When I go back and manually format the partitions, I get an option for sda3 (the Ubuntu root partition), but the OK button doesn't let me install it there.

I'm pretty new to Linux. Can anyone help me with this grub thing?

Here's my manually formatted partition table:

/dev/sda[INDENT]
/dev/sda1     efi     209 MB
/dev/sda2     hfs+ 291.92 GB
/dev/sda3     ext4  23.94 GB (mount point at '/')
/dev/sda4     swap 4 GB
[/INDENT]


Thanks! ;)

---

### Post by alphonce on 2010-08-07
i recently installed ubuntu on my imac and am fairly new to this aswell.
i installed everything from scratch beginning with mac os x.
when i installed ubuntu i also created a boot partition (128mb) with ext2 which i installed grub on. this is highly recommended, and its also easier to fix problems with the kernel. try that. =)

---

