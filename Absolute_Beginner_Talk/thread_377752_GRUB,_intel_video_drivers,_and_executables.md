---
title: "GRUB, intel video drivers, and executables"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Dood77 on 2007-03-06
Hi, i recently installed ubuntu 6.10 two days ago, its my first linux OS so obvioulsy i have some questions...
First of all how do i configure GRUB? where are the files located? when i installed ubuntu i wrote over a 4.5GB partition that was some system restore data for an old version of windows. so i have one 40GB ntfs drive for windows, and the other drive has one 34GB ntfs partition for storage and a 4GB partition for ubuntu and the .5 GB for swap. So naturally to boot ubuntu i thought i had to switch the boot priority from the windows hard drive to the other one. but when i restarted it gave me n Master Boot Record error, then proceded to load GRUB and gave me a choice of what to boot. I had no idea what the MBR was, so i recently looked it up on wikipedia, and i believe i get the gist of it, but i would appreciate if someone would explain it to me. Anyway after i switched the boot priority again back to the windows drive it just loaded up grub and didnt give me a choice, it just booted ubuntu. So i want to configure GRUB to ask me everytime what to boot, and have windows be the default.
Second, im having trouble with my intel 865G onboard graphics. I was stuck at a 640x480 resolution and 60Hz refresh (ouch)  i read that theres trouble with the driver and downloaded the 915resolution package an installed. it wouldnt let me choose the resolution until after i reconfigured the X server (i believe this is what it was, i was sort of following instructions blindly) i have the resolution i want, but i still have no other options for refresh rate other than 60Hz. Im guessing i have to alter the xorg.conf?
The third and last problem (i promise) ive downloaded and installed packages alright, but theres been a few programs that didnt come in an installer, and i run the executable and nothing happens, no error message or anything. the first one was the 915resolution program, but later i realized i could download a .deb package and it works fine. The other one was a Quake port, specifically EZQuake. I ran it on windows okay but when i downloaded and extraced the linux version into my quake directory and ran it, nothing happened. Is there something about executables in linux that im not getting?
Thanks in advance for the help :wink:

---

### Post by mikewhatever on 2007-03-06
MBR Link:  [http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)
GRUB Link:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Your swap partition is over sized. 1GB is more then enough, unless there are special needs. If you need help with GRUB and Windows loading, post the output of the following
> gksudo /boot/grub/menu.lst
gksudo fdisk -l

Normally, Ubuntu installer detects other OSs and puts an entry into GRUB menu to let you choose witch one to boot from.

---

### Post by Dood77 on 2007-03-06
Actually my swap is 0.5GB i forgot the 0 above so you probably missed the .
The link was very helpful, thanks. Apparently i missed the GRUB menu when i booted the primary drive and ubuntu was booted by default after 10 seconds. Its all configured now and working fine.

 Still looking for solutions to the other problems...

---

