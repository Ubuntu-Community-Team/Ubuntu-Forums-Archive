---
title: "[SOLVED] no IDE's installed after plugging in new dvd burner"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by bigbudz on 2008-04-11
I recently switched to Ubuntu from Win98 and I really like it. Just tried to replace my CDrom with  a DVD burner on this desktop, but disaster and now I can't load Ubuntu and am dead in the water... computer always retuurns 'Invalid Boot Diskette Insert BOOT diskette in A:'( Yes I still have a floppy drive, purchased this computer in 2000.) 

I went to bios and disabled the floppy as a boot device. Still same message. Even tried dissconnecting the floppy and got the same message. After reconnecting the old CDrom I still get the same message. 

When I get the computer to boot to the hard drive it displays the dell logo (which is weird b/c I formatting my drive and installed Ubuntu) then after about 10 sec it returns the same message about a boot disk in the floppy drive. 

In IDE config. It says the primary master and primary slave are not installed... these are my hard drives, i'm guessing this is not good. The secondary slave and master are showing ok as my cdrom and cdburner. Everything was fine before I tried to swap the cdrom for a dvdburner. Now the hardware is as before but Im still getting the boot disk message 

Can anyone help me please?

---

### Post by swoll1980 on 2008-04-11
did you double check that the cable is not loose or something sily like that

---

### Post by bigbudz on 2008-04-11
did you double check that the cable is not loose or something sily like that

Yeah I did, I first thought where that where the IDE connects to the motherboard must be loose, but its in  for sure. Everything is tight. I was thinking maybe its the cable itself, but there'd be no reason for it to go just like that. Someone else posted a few days ago that his hard drives weren't being recognized after he tried to install a IDE device. 

I have Ubuntu running from disk now, but it doesnt pick up either of my drives.

---

### Post by uberben on 2008-04-11
check all the drive's jumpers and make sure the cables are all snug. also, try putting the drives in a spare computer (if you have one) and see if that computer can read them. if not, it might be an issue with the hard drive. if it runs fine, odds are its something wrong with the rest of the computer.

---

### Post by joshrobinson on 2008-04-11
have you checked the jumper on the back of the new dvd drive? is it on the end of the IDE cable or the middle?

the one on the end of the IDE cable should be set as master, and the one on the middle should be slave

make sure your hard-drives and your cd/dvd drivers are right

---

### Post by bigbudz on 2008-04-11
> **joshrobinson said:**
> have you checked the jumper on the back of the new dvd drive? is it on the end of the IDE cable or the middle?

the one on the end of the IDE cable should be set as master, and the one on the middle should be slave

make sure your hard-drives and your cd/dvd drivers are right


The CDrom is on CS and on the end of the secondary IDE... recognized as master
CD burner is on Slave and on the middle of secondary IDE...      slave

Master hard drive on end of primary IDE
Slave hard drive on middle of primary IDE. 

Everything hardwarewise is the same as before, so all the drivers should be fine. But when I got Ubuntu to run from disk neither hard drive is recognized. In Bios both master and slave primary IDE are uninstalled. 

I have everything stored on the other hard drive, so a reinstall is an easy option if I could recognize the hard drives.

---

### Post by joshrobinson on 2008-04-11
have you tried removing your primary slave drive? and just trying to see if the master is recognized in the bios? then try plugging the slave back in and reboot, and see what happens?

sometimes things just get alittle goofy

---

### Post by bigbudz on 2008-04-11
> **joshrobinson said:**
> have you tried removing your primary slave drive? and just trying to see if the master is recognized in the bios? then try plugging the slave back in and reboot, and see what happens?

sometimes things just get alittle goofy

In bios IDE configuration both primary IDEs are showing as not installed with and without the slave hard drive plugged in. 

I'm still gettin the dell screen followed by a prompt to insert BOOT disk in A: even though I disable the floppy as a boot. At least it doesnt check it anymore.

---

### Post by bigbudz on 2008-04-11
my bad. I fixed it in a few minutes this morning. It was kinda late last night... The cable was loose, right where i said too. Ubuntu picked up the dvd burner after, no sweat. It won't recognize any CD's or dvd's burned on Vista tho, neither will my ancient latop running win98. Probably something with Vista Id say. Its ok b/c I can just burn in Ubuntu on my desktop for now.  

Im gonna run Vista - Ubunutu dual boot on the laptop eventually, but I'm gonna wait for Hardy Heron or maybe the next version after hearing some of the issues people had with the two. Even this cd thing makes me think its gonna be nothing but trouble. Plus I had a problem with Vista recognizing an external drive with ntfs. Ubuntu works perfect its Vista thats not compatable with anything. But who knows, Im pretty new to Linux now.

---

