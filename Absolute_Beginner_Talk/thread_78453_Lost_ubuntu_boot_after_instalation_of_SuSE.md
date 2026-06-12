---
title: "Lost ubuntu boot after instalation of SuSE"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Jefo on 2005-10-18
Before installing the new SuSE 10, with I didn't like becuase the applications crash too much (at least in my machine) and it's much more difficult to find good support in comparisom with Ubuntu, I had Ubuntu Hoary in hdb2 and Kubuntu Breeze preview in hdb1.

Kubuntu had the grub working for booting itself and Ubuntu, besides that "other" operating system in hda1. 

Well, during the instalation of SuSE, I couldn't manage to set the boot for Ubuntu in hdb2 because the system saw the partition as FAT32, although it was ReiserFS (pretty wierd :confused: ).

Is there any way of recovering the boot of Ubuntu, like using the instalation DVD of ubuntu, or SuSE SO itsef?

---

### Post by landotter on 2005-10-18
Ubuntu's perfectly recoverable. I think you can reinstall the bootloader with the install disc, by boot "parameter".

I don't remember what it is, but thought I'd post to calm your nerves. :D

Someone smarter than me will be along shortly with the details.

---

### Post by mlomker on 2005-10-18
That depends.  Is grub installed or some other boot manager?

I usually boot a Knoppix CD and then [reinstall grub.]("http://geodsoft.com/howto/dualboot/grub.htm#install")  If you have more than one operating system then you may have to manually edit your /boot/grub/menu.lst file to add the others in.

---

### Post by landotter on 2005-10-18
There are plenty of threads on this fwiw, just search for "restore GRUB".

Probably the easiest would be to boot the install CD, then to gain root access at the "boot:" prompt type "rescue" and follow the instructions.

Then to restore GRUB:
grub-install hda

That's assuming the bootloader was on the first boot partition of the first drive in your machine, which is the case almost all the time.

Do have a search though, there are other options.

---

### Post by Jefo on 2005-10-18
Guys, I have my Ubuntu boot back, but it's not like I resolved the problem...

Since I didn't like SuSE, I reisntalled Ubuntu (another) over it just to get the boot back to working. Don't blame me, I'm a beginner.

But thanks, landotter for the tips and mlomker for the reinstall grub link, I will study it, since I wanna try mandriva 2006 too and don't want the same problem to happen again.

---

