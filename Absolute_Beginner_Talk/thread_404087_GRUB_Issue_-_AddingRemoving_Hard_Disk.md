---
title: "GRUB Issue - Adding/Removing Hard Disk"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by futureal2032 on 2007-04-07
Hi,

actually i don't have any problems with my GRUB.... just asmall thing i wanted to know which i don't..


I have 2 - 80GB Hard Disks ..

Primary Master is a Seagate 80GB
Primary Slave is a Samsung 80GB

[B]I have WIndows XP on the first partition of my Primary Master (1st) Disk.

I have Ubuntu on my Primary Slave (2nd) Disk. I installed it  ina free space available on that disk..

Naturally have GRUB as the boot loader installed on my MBR...(which is on the first disk)


ALl i want to know is what changes to GRUB i should do before removing my second hard disk..to still be able to boot from Windows XP. 

Coz when/if i will remove my second disk..GRUB wont load properly since it wont find the boot options specified in it/OS on that disk (Ubuntu).... and i dont know much abt Grub to be able to open it in recovery console mode and boot to XP.

so is there any way where i can remove the second disk and still grub will launch properly and show my WIndows XP?
[/B]
i think...have taken too much space explaining a simple thing..but i would appreciate if someone helps me out here...

---

### Post by mac.ryan on 2007-04-07
If you don't need to re-insert the HD at a second stage, you can simply "fix" the MBR either from within ubuntu either from XP itself. I frankly don't remember the GNU/Linux command, but the one under XP is "[fixmbr.exe]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")".

This will remove GRUB, that can however be reinstalled from the LiveCD again, should you reconnect your second HD...

---

### Post by futureal2032 on 2007-04-08
thanx for the reply...

but the fixmbr.exe is to clean/remove grub and load the default windows boot loader ntldr...
i dont want that...as i want to remove the hard disk temporarily... 

why i asked this stuff in the first place...is 
even when ..suppose i attach my cd rom in the second hard disks place and attach the scond hard disk to secondary cable...

or even make the second disk master and first disk slave...then also grub wont recognise it...

so i need coomand/script or grub conf..so i can just make changes....
remove the disk temporary for work... restart and load Grub properly..use windows...

then later when i attach the second disk again... start ubuntu and load the default Grub config again..

---

### Post by al7kz on 2007-04-08
delete

---

