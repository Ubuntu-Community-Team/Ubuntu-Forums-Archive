---
title: "[SOLVED] Dual boot with windows Vista 32bit help"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by alarson82 on 2008-02-17
Please help!  I want to start using Ubuntu Linux to get away from windows for many many reasons that I don't need to get into now.

I followed the instructions at this website

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I have a 500 gb sata drive where my vista files are on.  I formatted about 80 gigs for ubuntu. Then loaded up the live CD (ubuntu 7.10) and installed the OS onto the new partition I created.

When I went to restart the computer, i got a message saying "no operating system found" (or something to that effect).  I put in my vista disk to try and repair the MBR, but that did not work.   I booted back up with the live cd, but it would not allow me to edit the grub/menu.lst in the partition that it was just created it.  Finally after many hours of poking around I opened up GParted and saw that the ubuntu partition was listed as 'boot'  so i changed it to the vista partition as boot. 

Restarted the computer and got my windows back.  Which is great but I couldn't/can't boot into linux because if I go back in (via live cd) and make the partition boot via gparted it will not boot into anything.

Any ideas?  Thank you

---

### Post by le1 on 2008-02-18
honestly you should try one more time:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

or

[http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

it gets little tricky once you get to "prepare disk space" but select "manual" and follow instructions.

---

### Post by alarson82 on 2008-02-18
Thanks for the reply.

I will try those later today or sometime this week.  hopefully i have better results

---

### Post by Bartender on 2008-02-18
Did you intend to let the Linux bootloader (GRUB) install to the vista MBR?  I ask this because it sounds like it did not install there.  If it had you'd have needed to fix the MBR before vista would work again.  Just changing the boot flag would not have been enough.

I've read good things about EasyBCD.  Haven't tried it myself.  But this might be the ticket for you.  Supposedly it installs to a vista system in a way that allows you to choose your OS at boot without messing up the vista MBR.  Or something like that.  Might be worth looking into..

Are you sure your LiveCD is 100%?  Did you run the "Check Disc" utility at the first splash screen?

---

### Post by kryth on 2008-02-18
You can try 

[http://www.vistabootpro.org/](http://www.vistabootpro.org/)

or 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

to fix it.

---

### Post by alarson82 on 2008-02-21
Well I used EasyBCD and was able to select what operating system I wanted to boot into at startup!!! YAY!!

However when i chose Ubuntu the grub was trying to boot from the wrong hdd (have 2 internal hdd's) I edited the hdd that it should boot from, it was trying (1,1) and i edited it to (0,1)  and it worked.

And luckily my wireless internet card was recognized and worked right away so i have internet.

Now to get my Nvidia 8800GT video card to work, thats my next challenge

---

