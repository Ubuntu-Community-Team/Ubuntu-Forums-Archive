---
title: "Trouble with Ubuntu / Grub and booting with SATA drives"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by will0957 on 2007-01-10
Here's my setup...

DFI Ultra II LanParty motherboard

2x 160gig SATA drives (sda, sdb)
2x 300gig standard IDE drives (hda, hdb)

I made a mistake and accidentally formatted the 2x 300 gig drives during an OS install. I have some very important data on these drives I need to recover. Luckily I haven't written anything on the drives after formatting.

Basically I have these 2x 160 gig SATA drives that I can use to install an OS on and I need to boot from them. If I JUST have the SATA drives in my machine and install Ubuntu, I can boot and have no problems. 

If I have either of the standard IDE drives installed, Grub won't boot.  For example, lets say I have the following drives connected and setup:

Ubuntu installed on sda
Nothing on sdb
Nothing on hda

Install ubuntu, restart, Grub will come up but say that there is nothing on the partitions. 

I can have just sda and sdb installed, then install ubuntu, and boot with no problems. 

It doesn't make any sense to me. Does anyone have any ideas?

---

### Post by geek_Man on 2007-01-10
Well, whatever you're doing is kinda confusing, but it can work. Boot with you're Live CD and change your menu.lst file. If that looks like visual static to you, go into the terminal and type: ```
cat /dev/"hard_drive_name"/boot/grub/menu.lst
```

The afore mentioned "hard_drive_name" is whatever drive that has your Ubuntu files (mine was usbdisk).
Copy the text and stick in "[CODE]" tags. And I'll have a look.

---

