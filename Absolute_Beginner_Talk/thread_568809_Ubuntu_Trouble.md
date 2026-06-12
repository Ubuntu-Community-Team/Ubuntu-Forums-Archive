---
title: "Ubuntu Trouble"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by DarkSaberLS on 2007-10-06
Hi my name is Mike, im pretty new to ubuntu, i recently got 2 laptops for myself they both have ubuntu installed on them but i want to install windows on one for my Girlfriend but i have a problem with doing so, i get the message below

"Cannot open /media/Y-BM62/setup/setup.exe: No application suitable for automatic installation is available for handling this kind of file. " 

if anybody could help me it would be a 1000 ton weight taken off my shoulders, that was a message from when i put a labtec mouse cd installer in because most of my cds arent being read apart from my music cds.

i do like ubuntu thats why im keeping it on my laptop :lolflag: but its for my girlfriend and i would to give her this.



Mike aka DarkSaberLS

---

### Post by Linux_Man on 2007-10-06
You must reboot to start Windows :) just put it in your CD drive, make sure the BIOS is set to boot from your CD drive first then follow the instructions, although Microsoft's bootloader will destroy GRUB and make it nearly impossible for you to access Ubuntu, so google that and make sure you know what will happen, also Windows can't read or write to ext3 partitions so none of your data will be readable from Windows.

---

### Post by Sbarton on 2007-10-06
If you want to clean install 'windows'  without any other OS on the laptop you can use the 'Live Ubuntu CD' or download G-Parted Live CD' to delete any partitions then install 'windows'.You might want to consider getting SP2 for windows before installing if (XP) or slipstreaming SP2 with XP if you are using that OS.
regards

---

### Post by Cannaregio on 2007-10-06
Just _ prepare a dual boot ubuntu+Windows_ for your girlfriend, so that she will be able to boot ubuntu when needed (as soon as windows crashes or gets infested with virii for instance).

Follow these instructions:

[http://ubuntuforums.org/showthread.php?t=358183&page=2]("http://ubuntuforums.org/showthread.php?t=358183&page=2")

Once you have dual boot, modify grub so that it boots windows in 5 seconds if she does nothing.

Good luck to your girlfriend, poor thing.

---

### Post by DarkSaberLS on 2007-10-06
I Dont think Ubuntu has anything that can read the windows disk its confusing me :confused: it cant read nrg files nor rar files and i cant find my iso windows xp so would ubuntu read ISO files from a disk ?

I liked the Fact i got help with 4 minutes lmao i think i need to get its internet connection sorted out if anyone else has anything to say it would be greatly appreciated

thanks Cannaregio lol

---

### Post by Sbarton on 2007-10-08
If you cannot find your windows xp disc your gonna have problems installing it  :). Seems you have 2 options here (1) buy another Windows copy (OEM), (2) Convert your girlfriend to Ubuntu  and help her widen her OS experience. If you do reinstall windows try what 'cannaregio'
has mentioned in his post about Dual Booting. One other point Mike, Ubuntu linux won't open/install .exe files as far as I am aware, I stand to be corrected here.I know some windows items may work with 'Wine' installed but I know little about 'Wine' as I do not use it.
regards

---

