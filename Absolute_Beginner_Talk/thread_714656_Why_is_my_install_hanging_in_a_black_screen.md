---
title: "Why is my install hanging in a black screen?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by kindlyaware on 2008-03-04
Ok so as far as I can tell I've done everything right as far as shrinking my HD down to make room for Ubuntu.  I've followed every instruction I can find to install 7.1 as a dual boot and after all my trouble I am getting held up after the scrolling to a blank screen with an occasional flashing cursor at the top left.  I am running an eMACHINE (don't hate :P) w3644 32 bit with like 4 gig ram and an 8600 series Nvidia card

Can anyone provide some suggestions to get Ubuntu up and running on my system, or perhaps another beginners distro.

---

### Post by articwolf939 on 2008-03-04
are u tring to dual boot with window and if so what one vista or XP or later?

---

### Post by uberlube on 2008-03-04
During the boot process you may have to specify what type of vga your monitor is to use, until you get into the OS for the first time and install your video card driver. To specify, edit the boot process and delete 'quiet splash' and add 'vga=791'. Give that a try and let me know if it works.

---

### Post by zvacet on 2008-03-04
If you can access terminal with Ctrl+Alt+F2 then in terminal 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select **nv** driver and if this doesn´t work try again and select** vesa **driver.Later you will find driver for your card.But if you can not access terminal this way boot in recovery mode and type same command without **sudo**.

---

### Post by kindlyaware on 2008-03-04
I am using XP.  I will try your suggestions tonight.  Thank you.

---

### Post by dmich on 2008-03-04
I have exactly the same problem with the black screen and the blinking cursor at the top left corner.
The problem is that I am using the windows xp boot loader and not grub to do the dual boot so I can't do any of the suggestions here...

is there any ways to change the booting options as suggested from the livecd ?

---

