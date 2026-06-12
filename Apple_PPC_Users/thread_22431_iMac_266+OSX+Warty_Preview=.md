---
title: "iMac 266+OSX+Warty Preview=?"
date: 2005-03-27
forum: Apple PPC Users
---

### Post by swat42572 on 2005-03-27
So here's my story...

I dropped a 120 GB hard drive into my 266 G3 iMac a couple of months ago, reinstalled OSX and partitioned it three ways in OSX's Disk Utility: a 7.5GB HFS+ partition at the top of the partition table for OSX, having read that my vintage of iMac will recognize OSX only if it's installed on a partition that's 8GB or less at the top of the disk table; an 80GB HFS+ partition to hold documents, etc.; and 20GB of free space at the end, with the intention of installing some form of Linux and being able to dual boot.

Fast forward to the present day; I have a functional copy of the Warty install disc (and by functional, I mean that my flaky CD-ROM drive will recognize it without errors ;-) but that's a different topic for another forum thread...)  I start the install process, have the installer automatically set up that 20GB partition the way it sees fit, and the install process went along its merry way....until it came time to restart my computer for the second part of the install process.  Bingo, blank screen.  Yaboot, evidently couldn't see either system partition.  I went ahead and reset the PRAM, rebooted, and got the folder with a question mark, which would mean that my OSX system wasn't being recognized either.

I am writing this using the Warty PPC Live CD, on the non-functioning computer.  I don't know how I would be able to view the complete partition table on my hard drive at this point.

Any advice or suggestions on getting something to boot up here would be greatly appreciated.

---

### Post by swat42572 on 2005-03-27
And after I posted, I remembered that it's the Hoary Preview that I'm running...so substitute "Hoary" for "Warty" in the previous, and things will be just fine #-o

---

### Post by DJ_Max on 2005-03-27
try to boot up with the option button press, then see if you can boot Ubuntu. If you can, post your /etc/yaboot.conf

---

### Post by swat42572 on 2005-03-27
[QUOTE=DJ_Max]try to boot up with the option button press, then see if you can boot Ubuntu. If you can, post your /etc/yaboot.conf[/QUOTE]

I tried that, and no dice...just the same flashing folder, and then the folder with the question mark.

---

### Post by erkki70 on 2005-03-27
Hi,
 I've been running same config as you but with a smaller HD and OSX, OS9 and Debian Sid at the same time.
The issue of having the boot system in the first 8GB of the drive on this specific PowerPC G3 architecture does apply for all *NIX based Operating Systems. Therefore your Ubuntu Hoary must be located within those first 8GB of your drive, or at least your "/", "Home" can be located somewhere else.
 It cannot be located at the end of your drive and has to follow the OSX partition.
 
 [http://www.lowendmac.com/10/01/1130.html]("http://www.lowendmac.com/10/01/1130.html")
 
 This will help and explain, this is a known issue on those machines.
 
So what I did was partitionning my HD to have 2 partitions within the first 8GB of my HD, 6,5GB for OSX, followed by another 6,5GB for Debian Sid (so here fits your Ubuntu and it can be bigger partition if you wish), then several partitions for wether OSX or Debian Sid or both on Exchange.
 
You can try like this, eg OSX 7.5GB first on HD followed by Ubuntu whatever size you want, and the rest. Note that if you still have problems you might have to decrease your OSX partition size to allow your Ubuntu partition not to be so close of the 8GB limit.

By now, after zapping the PRAM several times, even though you see the folder with a question mark, your system should automatically switch to OSX an boot normally.
Anyway if you see this instead of yaboot, it probably means that you can safely recover with OSX cd and fix it all with OSX tools.

 Hope this can help.

---

### Post by swat42572 on 2005-03-27
erkki70, thanks for the added info.  That will be something I'll attempt when I've got a free day (or two) and the Hoary release version in my hot little hands (and the contents of my Home directory backed up...)

The second part of my inquiry involves my computer not being able to boot into OSX.  Any tips in that realm, short of reinstalling OSX as I am away from home and access to my Panther install disks, would be most helpful as well.

---

### Post by erkki70 on 2005-03-27
[QUOTE=swat42572]
The second part of my inquiry involves my computer not being able to boot into OSX. Any tips in that realm, short of reinstalling OSX as I am away from home and access to my Panther install disks, would be most helpful as well.[/QUOTE]

First try to boot your mac in safemode eg, single user mode (google is your friend and you'll find all the useful commands to repair if needed)
Well, you can also try to boot you Imac in the open firmware O+F+Apple+Ctrl+Shift (or Alt, you have to check this combination of keys!) then at the prompt type: boot. ```
boot hda4
``` the number is where your osx is located on the partitions. Though it might give the same results eg. question mark folder.
If you remember the partition number where yaboot has been installed at the prompt type: boot hda(the number of the partition where yaboot is), yaboot. eg, ```
boot hda3, yaboot
``` 
If it launches yaboot correctly, you can choose to boot OSX from the first menu by quickly pressing X or M if you have OS9 installed too.
Be very cautious as mac firmware is like bios and you can easily mess up!

I would recommend, 1 safemode, 2 OSX install CD, 3 firmware commands.
Good luck

---

