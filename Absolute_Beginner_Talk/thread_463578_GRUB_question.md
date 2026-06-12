---
title: "GRUB question"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by R00tBreaker on 2007-06-03
I just installed ubuntu 7.04. I dual boot between linux and XP and I just have a quick question. When I start the computer and the GRUB menu appears, it lists Ubuntu and Ubuntu recovery mode twice. It looks like this:

Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

Other operating systems:
Windows XP Media Center Edition
Windows NT/2000/XP

Making an educated guess, the reasons for the two different Ubuntus is that they use a different kernel, correct? Which one should I be using? And why does it list NT/2000/XP as one of the different OS's?
Thanks for the help

---

### Post by drs305 on 2007-06-03
You are correct. If you look closely you will see that Grub has listed two kernels, the latest (16) and the previous one (15). Normally you would use the latest kernel and that is what grub will boot unless you change it. It displays older kernels in case you have problems and wish to revert to an older (and presumably working) kernel.  You can select which kernel you wish to use during boot when the grub menu is displayed. 

There are ways to hide previous kernels as well as setting the timeout and which OS grub automatically selects. You can easily find how to edit grub in other posts on this site.

---

### Post by Liakath on 2007-06-03
> **R00tBreaker said:**
> I just installed ubuntu 7.04. I dual boot between linux and XP and I just have a quick question. When I start the computer and the GRUB menu appears, it lists Ubuntu and Ubuntu recovery mode twice. It looks like this:

Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+

Other operating systems:
Windows XP Media Center Edition
Windows NT/2000/XP

Making an educated guess, the reasons for the two different Ubuntus is that they use a different kernel, correct? Which one should I be using? And why does it list NT/2000/XP as one of the different OS's?
Thanks for the help

Dear R00tBreaker,

Can you please put the out put of

sudo nano /boot/grub/menu.lst
or
sudo gedit /boot/grub/menu.lst

This may help us to resolve why the Windows is listed twice. May be you had earlier upgraded Windows 2000 / Windows XP to Windows XP Media Centre Edition

---

### Post by R00tBreaker on 2007-06-03
Before repartitioning and installing linux, my hard drive already had a second partition put on it by HP on which all of the recovery software was. They did this instead of giving me rescue disks. Perhaps this could be the reason windows is displayed twice?

---

### Post by icechen1 on 2007-06-03
> **Liakath said:**
> 

This may help us to resolve why the Windows is listed twice. May be you had earlier upgraded Windows 2000 / Windows XP to Windows XP Media Centre Edition

I also have this,The last one is for a recovery tool.

---

### Post by Liakath on 2007-06-03
> **icechen1 said:**
> I also have this,The last one is for a recovery tool.

Thank you icechn1 for the info on the "recovery tools" put by manufacturer.

---

### Post by Inxsible on 2007-06-03
I have a HP laptop too, but I nuked the recovery partition since I knew, that the day my Vista goes bonkers, I am gonna give it a boot (pun intended ) and go solo on Ubuntu

:)

---

### Post by icfriar on 2008-05-31
Thank you. This answered a similar question I had.

---

