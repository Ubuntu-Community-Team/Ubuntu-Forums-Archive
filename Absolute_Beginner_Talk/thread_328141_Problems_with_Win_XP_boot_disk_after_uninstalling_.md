---
title: "Problems with Win XP boot disk after uninstalling Ubuntu"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by MysteryShopper on 2006-12-30
Hi.  I've removed Ubuntu from a box which my wife will be using so that I can put XP on it.  (Don't worry - I'm putting Ubuntu on another PC staright away!).  Trouble is, my Win XP install disk (it's an official multi-licence CD which I've used successfully a number of times) goes through the blue-screen part of the install and then tries to reboot to go into the graphical part of the install, but never gets there.  If I leave the XP CD in, it just loops round and round without ever getting to the Windows logo splash screen.  If I take out the XP CD, it just sticks at the first boot sequence screen.  I've tried changing the oreder of the boot device sequence in the BIOS and I've tried fixmbr from the Recovery Console option in the XP install.

Any ideas?  Is Ubuntu leaving something behind which it expects to see during the boot but which is no longer there because I've run fixmbr or because I've reformatted the HDD?

Thanks.

---

### Post by steve.horsley on 2006-12-30
fixmbr should have replaced the GRUB bootloader. 

I wonder if the problem is that the installer finds that there is no suitable partition to install to (and no space to make one). Have you deleted the Ubuntu partitions? If not, I suggest you use the Ubuntu live CD, start the partition editor (System->Administration->GNOME Partition Editor) and delete the Linux partitions. 

If that's not it then I'm stumped.

---

### Post by oilchangeguy on 2006-12-30
you don't need to use the linux cd to delete the linux partition. you can do that with the windows cd. what do you mean "official multi-lic copy" theres no such thing. when you install the windows cd press any key to boot from the cd, follow the prompts to get to where it shows the linux partition, follow the steps to delete this partition, then follow the steps to install xp, format the drive ntfs, no quick format, let it check the drive for problems. then proceed with the install.

---

### Post by graficus on 2006-12-30
I'll join in with a related question. 
Would it be a good idea to "grub-remove" before doing this?

By the way, I downloaded something called Hiren boot CD, its a life saver full of useful utilities, including a few boot fixers. Guess you could try that.

---

### Post by oilchangeguy on 2006-12-30
no, this would make no difference. when you install an os be it windows or linux you have the option of deleting the partition used by the old os, and create a new partition to install on.

---

### Post by bigken on 2006-12-30
you have a bad disc my friend try and make an iso of it in ubuntu and burn a new copy ;)

its worth a try

---

