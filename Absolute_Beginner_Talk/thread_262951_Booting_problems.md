---
title: "Booting problems"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by D10 on 2006-09-22
This might be a problem with grub, but I am not for sure.

I installed the linux-686 package and was using linux kernel 2.6.15-26-686, and have been using it for awhile. Yesterday I upgraded to 2.6.15-27-686, and again all was well.

Today I was changing either icons or window manager settings, and my machine crashed. Some parts of the desktop were responding, but I was unable to open any new programs or close any open programs. I let the machine set for an hour just in case it might start responding again, and it didn't. Well the only way I seen to fix it was a hard reset, and start again. The problem is after it rebooted I can no longer boot using any of the 686 kernels. I have had something like this happen before, and completely removed all the packages for the kernel, and reinstalled and was back in business.

I tried that today as well, and no dice. I can still pick a 386 kernel from the grub boot menu and boot fine, but if I pick any 686 (recovery or not) it starts booting and then reboots the machine about the time the splashy boot screen should start.

I am not very knowledgeable in grub, or the linux boot process so I could be  calling items by the wrong name. 

Anyone have an idea where I should look? :confused: 

I am using xubuntu 6.06.1 if it makes a difference.

Thanks,
D10

---

### Post by D10 on 2006-09-25
bump

---

### Post by bulldog on 2006-09-25
I should boot up a 386 kernel and re-install the 686 if you want.

There's clearly something wrong but can't say what it is.

Could it be splashy to make your computer restart?
I had it once installed and it was terrible to look at,but it didn't restart my computer,but it was not very stable.

Try reinstalling 686 and if the problems re-occur come and pay us a visite,so we can talk about it.

---

### Post by haxer on 2006-09-25
bulldog word dawg :cool:

---

### Post by andb on 2006-09-25
Could you post your /boot/grub/menu.lst and the results of ls -l /boot/ please? Immediately after grub do you see the initial text flash for a fraction of a second or does it just restart?

---

### Post by D10 on 2006-09-25
> **andb said:**
> Could you post your /boot/grub/menu.lst and the results of ls -l /boot/ please? Immediately after grub do you see the initial text flash for a fraction of a second or does it just restart?

I will have to reinstall the 686 package to get the menu.lst and such, but before the machine would reboot it would flash the initial text.

---

### Post by D10 on 2006-09-25
OK well I guess nevermind for now. The other day when this problem happened I completly removed and installed the linux-686 package twice, and I could not get it to boot. So I uninstalled it, today when I reinstalled it it worked.:confused: 

thanks 
D10

---

