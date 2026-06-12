---
title: "Help with GRUB error 17"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-06-19
Ok, I had Ubuntu working properly for a while, but recently I began getting some errors:  At first, I wouldn't be able to log on.  So I went into the failsafe terminal, and entered ```
sudo apt-get clean
```and the problem was fixed.  Then I began getting that "Xauthorization" error when I tried to get into Synaptic.  I resolved this be simply logging off and on again. Then I tried to go into Synaptic again, at it worked, but it said that I had three broken installations.  They all had things to do with Linux, and I believe one of them said something about the kernal.  Finally, I tried to restart the computer, and when I tried to boot Ubuntu (I dual boot with WinXP), it gve me an error, "GRUB Error 17".  So.  Can anyone help me figure this out?  

Thanks.

---

### Post by dbbolton on 2007-06-19
you might need to reinstall grub. this link will explain how to do that from a liveCD

[http://ubuntuforums.org/showthread.php?t=320216#4](http://ubuntuforums.org/showthread.php?t=320216#4)

---

### Post by Yes on 2007-06-19
GRUB works and all, its just that when I go to try and boot Ubuntu from the GRUB menu, it says "GRUB error 17:  Cannot mount selected partition".

---

### Post by maddot on 2007-06-19
that partition could be corrupted. pop in a live cd... can you mount it?

---

### Post by brim4brim on 2007-06-19
Its probably the Grub list file thats messed up.  Look it up on a live CD version and see what the story is with it.

---

### Post by Yes on 2007-06-19
What would I be looking for/how would it have gotten messed up?

---

### Post by Yes on 2007-06-19
And does anyone know what all the other errors I was getting are all about?

---

### Post by logos34 on 2007-06-20
Yes, 

the best way to try to solve this is to have a look at /boot/grub/menu.lst.  Post it.  If you updated linux-headers- or linux-image-  or anything related to the kernel then menu.lst could have gotten screwed up.

---

### Post by drivel on 2007-06-20
> **Yes said:**
> GRUB works and all, its just that when I go to try and boot Ubuntu from the GRUB menu, it says "GRUB error 17:  Cannot mount selected partition".

Then,the partition on your computer must be changed,such as add a hard disk or remove one can cause this happen.
When the Grub show the boot menu,press "e" to edit the menu and press "e" when the highlight is on "(hdX,X)"
and retype them use tab button for help

---

### Post by KhaaL on 2007-06-24
> **drivel said:**
> Then,the partition on your computer must be changed,such as add a hard disk or remove one can cause this happen.
When the Grub show the boot menu,press "e" to edit the menu and press "e" when the highlight is on "(hdX,X)"
and retype them use tab button for help

This worked like a miracle for me, thanks a bunch! :KS

---

