---
title: "GRUB Error 21"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by srheath65 on 2006-04-08
I have a XP install on my primary drive and I'm trying to do a Ubuntu install on my secondary drive (slave). This installation seems to go prefect until the system installs Grub and then reboots. I get a "error 21" and then it hangs. I can't find a way around it. I ended up just using my XP install CD "R" (repair) option and repairing the master boot record. 

Since Ubuntu does not give me any other boot manager option during the install I can't try those. I also tried a floppy boot of "smart boot manage". This just either boots to XP or the "error 21" depending in which drive I select.

I need a way of fixing the Grub on the secondary drive either from within Windows or **a way of installing Ubuntu that will not install a failed Grub**.

I noticed several others are getting this error by doing a Google search but I could not find a solution that did not go over my head.

---

### Post by srheath65 on 2006-04-08
Good point srheath65. Sounds like this is a real problem. Someone please help srheath65. He sounds like a nice guy.

---

### Post by catlett on 2006-04-08
I don't know much but since noone else has posted I thought I'd give a suggestion. Lilo is the other boot loader used by Linux distros. Ubuntu doesn't give you a choice but it might be worth a little Googling to see if you can install Lilo by booting to a floppy. Or if there is a way to install Lilo other than a default install during an installation. Sorry I don't know more.
 If you don't get any of the gurus to answer you later I'll try and do a little lilo research. Good Luck

---

### Post by matthewv on 2006-04-08
You could try restoring grub over the messed up one.. that might help. Search the forums for a few guides on how to do this, or post here if you want my version :)

---

### Post by Mustard on 2006-04-08
deleted

---

### Post by patrick295767 on 2006-04-08
Hi man, 
  
This grub 21 is not very well documented. 
You'll have to fight with it.
  
I had it once and solve it as follows: [http://www.ubuntuforums.org/showthread.php?t=64557&page=7&highlight=grub+21](http://www.ubuntuforums.org/showthread.php?t=64557&page=7&highlight=grub+21)
but this was for vmware

 Greetz

---

### Post by catlett on 2006-04-08
I never heard of this open source bootloader but it appears you can install it to a flash drive and most importantly install it after your install is done.[http://sourceforge.net/projects/u-boot/](http://sourceforge.net/projects/u-boot/)
 I might give this a try because my Grub configuration is a mess right now. I have 2 phantom entries , 3 real entries to working OSs and 1 working OS not recognised.
  I was getting error 17 out of the blue last week. So I installed another OS and let Grub be re-installed. There is no longer an error 17 and I can boot to 3 out of 4 OSs, so I guess I'm not doing too bad. Hey if a Baseball player went 3 for 4 he'd be MVP.

---

### Post by dylonium on 2006-04-08
Is this a USB secondary drive? If so, follow the directions on this link- [http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external+hd]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external+hd")

---

