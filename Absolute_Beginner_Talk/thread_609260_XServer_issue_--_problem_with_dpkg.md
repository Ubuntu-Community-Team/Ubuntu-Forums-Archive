---
title: "XServer issue -- problem with dpkg"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by tjrm on 2007-11-10
Used Wubi to install Ubuntu (Feisty 7.04 alternate iso) for my first trial yesterday. Xserver does not work -- as I expected because of Nvidia GeForce FX 5200 256MB PCI card. Have been reading and searching the forums for a few weeks as I prepared for this trial. Have a Dell Dimension 2400 533 MHz processor, 1G of RAM, Dell E153FP flat screen monitor, and have Windows XP Home OS.

When I get past failure of XServer to CLI, enter username and PW, then try sudo dpkg-reconfigure -phigh xserver-xorg, and enter pw again, I receive message that it is making a backup (in /etc/x11/), but only get another $ prompt, no interface for changing device to vesa.

I tried without the -phigh parameter with same result.

I also tried nano /etc/x11/xorg.conf and was placed in a the editor, but it was a new file, with nothing to modify.  

I have seen suggestions about booting into recovery mode or into safe graphics mode, but I don't know how to get that option on this Wubi install.

Thank you in advance for  suggestions.

---

### Post by mikewhatever on 2007-11-11
One thing I know for sure is your xorg file is there, just use capital X, in other words, /etc/X11/xorg.conf. Linux terminal is case sensitive.

---

### Post by kmac on 2007-11-11
> **tjrm said:**
> 
I have seen suggestions about booting into recovery mode or into safe graphics mode, but I don't know how to get that option on this Wubi install.

Thank you in advance for  suggestions.


Get to your boot screen by pressing esc, f8, or f2 during bootup. (it's different with each manufacturer of computer). Then select ubuntu-generic (recovery mode). you'll be root so no need for sudo just

dpkg-reconfigure xserver-xorg

--Kyle

---

### Post by tjrm on 2007-11-11
Thank you both for your suggestions! I was able to edit the xorg.conf and get to the GUI on my last try. :)

---

