---
title: "How to remove ubuntu &amp; GRUB without windows CD"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by quecoder on 2008-04-17
Hello , 
i got this from linuxforums . com  when searched for "how to uninstall ubuntu / grub ) :

> 
1. Edit /boot/grub/menu.lst and change the default OS to Windows. In fact, you can delete the entries for Ubuntu if you like, and set the countdown timer to 0, so that it just goes straight to Windows without prompting.
2. Boot with the Windows CD, choose the Rescue option, and do a fixmbr. This is supposed to overwrite GRUB with the Windows boot loader.



Now , the first option will not be helpful cause I don't have a windows installation CD  to get to recovery console and doing fixmbr ...my laptop came with a recovery CD that just installs windows silently , just clicking next after inserting the CD ( without any buttons or other options ) , wait for 20 minutes and I have a fresh windows install ..
How can I get to the recovery console to do  fixmbr :(:confused: .. ?

so ,will the second option be helpful for me ?? and how to do it ( from ubuntu ) ?

---

### Post by Oldsoldier2003 on 2008-04-17
> **quecoder said:**
> Hello , 
i got this from linuxforums . com  when searched for "how to uninstall ubuntu / grub ) :




Now , the first option will not be helpful cause I don't have a windows installation CD  to get to recovery console and doing fixmbr ...my laptop came with a recovery CD that just installs windows silently , just clicking next after inserting the CD ( without any buttons or other options ) , wait for 20 minutes and I have a fresh windows install ..
How can I get to the recovery console to do  fixmbr :(:confused: .. ?

so ,will the second option be helpful for me ?? and how to do it ( from ubuntu ) ?

If you dont have the windows CD you could always download a boot cd or recovery cd that has fdisk on it. just do fidsk /mbr and it will remove grub and allow windows to boot from its bootloader. This is assuming that you are running Xp , I'm not sure if it works with Vista but i do know from personal experience that it will with XP.

---

### Post by arochester on 2008-04-17
You can download and use freedos. It is mentioned by saikee here: [http://www.linuxforums.org/forum/mandriva-linux-help/83953-grub-error-21-a-2.html](http://www.linuxforums.org/forum/mandriva-linux-help/83953-grub-error-21-a-2.html)

---

### Post by bumanie on 2008-04-17
Try what  Oldsoldier2003 has suggested, otherwise, you will have to use super grub disc or test disk to rewrite windows mbr. Can't help more as I've never needed to do it. [Super grub disc]("http://supergrub.forjamari.linex.org/?section=download") Test disk is [here]("http://www.cgsecurity.org/wiki/TestDisk") They apparently work.

---

### Post by quecoder on 2008-04-17
Oh , i'm afraid to mess with that , I'm a real n00b .. :( isn't there any simple steps to remove the Grub from within widnows XP  !?

---

### Post by forrestcupp on 2008-04-17
Super Grub is very useful to restore the Windows boot loader.  But [here is a post](http://ubuntuforums.org/showthread.php?t=622828) that tells how to do it using the Ubuntu Live CD that you already have.

---

### Post by bumanie on 2008-04-17
You could probably find a way to remove grub form windows mbr, but it would leave you with a corrupted mbr and windows would not boot. You will have to fix windows bott and mbr somehow. Could you possibly borrow a disk from a friend? Are you using xp?

---

### Post by quecoder on 2008-04-17
> **forrestcupp said:**
> Super Grub is very useful to restore the Windows boot loader.  But [here is a post](http://ubuntuforums.org/showthread.php?t=622828) that tells how to do it using the Ubuntu Live CD that you already have.

thank you for replying .. But is Super Grub easy to use to remove the grub in my case ?? is there any tutorial on how to use it for this purpose ...??

---

### Post by forrestcupp on 2008-04-17
Just boot to the Super Grub CD and it should be obvious through the menus to see how to restore the Windows boot loader.

---

### Post by Oldsoldier2003 on 2008-04-17
> **forrestcupp said:**
> Just boot to the Super Grub CD and it should be obvious through the menus to see how to restore the Windows boot loader.

Agreed. One of the advertised uses of supergrub is that it is a learning tool for grub

---

