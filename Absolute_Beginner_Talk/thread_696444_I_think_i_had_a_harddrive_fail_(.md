---
title: "I think i had a harddrive fail :("
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-14
was unable to boot computer said error loading OS when tring to start grub
tried to repare the mbr didn't fix it 
install linux on other drive 
right now i am running badblocks on all partions of the drive

i tryed to boot linux off of the drive useing the grub on my second hard drive didn't work
can see files on the bad drive it has not completly fail yet 

so what do i do if badblocks returns that all of the blocks are ok

---

### Post by macogw on 2008-02-14
The other thing to check is to install smartmontools and see what the disk is reporting from SMART ```
sudo smartctl -a /dev/<disk>
``` Put in /dev/sda or /dev/sdb or whatever it is.

If there are no bad blocks or sectors (SMART reports those as "reallocated sectors", read the far right column), then it's possible some important file became corrupted, perhaps from powering off without shutting down properly.  If that's the case, backup, format, reinstall.

---

### Post by bumanie on 2008-02-14
It is quite probable that your hard drive is OK, it is most likely some type of grub error that is preventing you from loading any OSes.  Are you receiving a grub error when you are unable to boot? Your best bet is to go download a copy of super grub disk live cd from here [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/) and see if that helps, if not go here and read about grub problems   errors and fixes [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-14
well i had both linux and windows on the drive 
both will not boot and could not get eather to boot after i installed grub on the other drive and tried to use that to boot off the first disk
so i dont know
i did reinstall linux on it 
the installer made it all the way through but it still got the same error 
right now the drives are set up so the "other" drive is the master and the broken one is the slave it would not get past bios things when the only drive connected is the broken one
but i still didn't find any badblocks
got to go to bed now will tell you all more tomarow

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-14
right now i can read of the drive and right to it 

can not boot from it when its in the master 
--> think this means bad mbr not just grub becuses i have all ready tried to repare grub and it didn't work,

can not boot from it when its in the slave and i have a nother drive with grub install on it with the location of windows or linux on the "bad disk"  
---> dont know what that means

I did make room on the good disk for a partion the size of my windows partion on the bad disk
i used this comand
```
sudo dd if=/dev/hdb1 of=/dev/hda1
```
this dumps bit by bit, i gess, the data on hdb1 "the bad disk windows" into the hda1 part
so then i told grub to try and boot from the hda1 part "new windows" and it did
i have my windows back

not worried about my linux install all of the files that were in home are on the good drive

and badblock didn't find any bad block on any of the partions
how ever the fist and last partions are ntfs and i dont know if it checks them the same

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-15
I hate to say it   .........       bum

---

### Post by bumanie on 2008-02-15
What type of hard drives do you have? IDE or SATA and which brand? I know that a small numberof ide seagate drives seemingly have firmware which is not compatible with ubuntu. I too have a similar problem to you, where one drive works fine if it is plugged in by itself, but won't work if both drives are plugged in together. I can't exactly say for sure that it is the seagate drive's fault, but I suspect it may be as I have read about this problem on a couple of occassions. It doesn't seem to happen with seagate sata drives though. I get around it by booting with super grub disc, even though grub sees my windows drive/partition correctly and the ubuntu drive/partition correctly, it won't boot - only gives grub errors. For some reason, I can't work out, super grub disc will boot the comuter correctly (ie SGD doesn't do anything that grub commands can't do, but in this instance it seems to). My /boot/grub/menu.lst is correct. If I were you, I would try super grub disc and see if you can boot with it. I know it is not a perfect fix, but at least if you can boot, it's a start.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-25
It was a Western Digital 120 gb. Has to be at lest 5 years old, but probably more like 10. Really saying 8ish. Any way it is definatly dead.

---

### Post by tango_ninja on 2008-02-25
I had this sort of problem on my Gateway laptop, formerly running XP.....

something went wrong in the HD, and all of a sudden the sectors containing the system files & drivers disappeared, and I could no longer get winXP to detect any HD.

I booted with linux and was able to repair using **fsck** from the command line at boot.....

do you have this option?

---

