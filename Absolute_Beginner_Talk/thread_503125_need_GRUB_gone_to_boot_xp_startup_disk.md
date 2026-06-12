---
title: "need GRUB gone to boot xp startup disk"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by gkabbott on 2007-07-17
i need to stop grub from working to get my xp startup disk to load. i used gparted and microsoft says this will leave the root in tact, hence formatted harddrive, but grub still exists. please don't tell me to go to bios and make the diskdrive first ahead of the harddrive. we are way past that. gparted did not kill grub. microsoft said something about the root. how do i disable grub to read a bootable cd. and why can it boot gparted, or the ubuntu startup cd, but any other bootable cd and it gives it a sniff, but won't start it. ubuntu is not for me, we are they trapping me in it with grub. grub must die, How??

---

### Post by wolfen69 on 2007-07-17
grub will not prevent you from booting to cd. ive never heard of this. just get a drive wiping utility and zero the drive if you want everything gone.

---

### Post by jombeewoof on 2007-07-17
you need to fix your mbr by booting to your windows cd, using the recovery console and typing 
```
fixmbr 
```
at the dos like prompt.
grub wouldn't cause your bootable disks to not boot, If your system is set to boot from cd, the cd boot fails before grub even loads.

Edited command to actually work,

---

### Post by oilchangeguy on 2007-07-17
> **gkabbott said:**
> i need to stop grub from working to get my xp startup disk to load. i used gparted and microsoft says this will leave the root in tact, hence formatted harddrive, but grub still exists. please don't tell me to go to bios and make the diskdrive first ahead of the harddrive. we are way past that. gparted did not kill grub. microsoft said something about the root. how do i disable grub to read a bootable cd. and why can it boot gparted, or the ubuntu startup cd, but any other bootable cd and it gives it a sniff, but won't start it. ubuntu is not for me, we are they trapping me in it with grub. grub must die, How??

first make sure the bios is set to boot from the cd drive. and are you using a factory restore cd? or a windows only cd?

---

### Post by ajgreeny on 2007-07-17
Have you got more than one hard drive, and did you install grub on a different one to your windows hard drive?  This may have some bearing on things, though I agree that if you set to boot from CD first, it shouldn't really make a scrap of difference; grub shouldn't appear at all in that situation.

---

### Post by neopentrix on 2008-04-23
hey,

i have the same problem. i am tryin to reformat my xp partition on my laptop (1 HDD) but cannot. currently it has ubuntu gutsy and winxp pro.

so the problem is booting off the xp cd. i stick in the xp cd and it tells me to press a key to boot from cd. when i do, it says its checking the hardware or watever and then goes to a black screen. cd drive stops spinning but my hdd light stays lit. i know its not my cds (ive tried several variations including pro sp1, sp2, and the original home edition from hp) because i have tried them on another computer b4 and i know it is not my cd drive cause i just replaced that a few months ago.

o yea, my ubuntu cd will load and my windows (from hdd) will boot and run normally. i just cant boot from the cd to reformat. and i dont want to reformat the whole drive cause i have a data partition. any ideas about a solution?

---

### Post by lkraemer on 2008-04-23
Well, I've been there.....done that.....

Best thing to do is to get yourself a copy of SUPERGRUB.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)      old web site.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
This site tells you everything you will ever need to know
about Dual Boot.  Good Reference information.

Make yourself a floppy and boot it and repair the 
Windows Partition.  Supergrub will remove GRUB and let
Windows boot.  Read the Documentation and give it a test.
Worked for me.

LK

---

### Post by adrian15 on 2008-04-24
> **neopentrix said:**
> 
so the problem is booting off the xp cd. i stick in the xp cd and it tells me to press a key to boot from cd. when i do, it says its checking the hardware or watever and then goes to a black screen. cd drive stops spinning but my hdd light stays lit.

Can you please confirm me that after using the "Fix Boot of Windows" option from Super Grub Disk you are able to use your xp cd (installation or whatever disk) again without a black screen?

This would be another use for SGD that I was not aware of.

Thank you.

adrian15

---

