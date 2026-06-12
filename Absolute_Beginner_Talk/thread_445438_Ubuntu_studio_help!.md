---
title: "Ubuntu studio help!"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Pnp1434 on 2007-05-15
I installed ubuntu studio on my laptop (compaq presario V6000 series  with Nvidia G force 6500 graphics card) with out any hassle but the problem is after installation and subsequent reboot, the screen went blank after the loading bar!. I tried it again by restarting but same thing happens.Please help!

I had previously tried to load Ubuntu 7.04 on the same laptop but failed since the installation stalls at 90%!
I desperately want to install Ubuntu on my laptop since I have been hearing a lot about it and wanna experience it first hand.

---

### Post by Gmbrdilos on 2007-05-15
did you try live CDs on that laptop previouslly?

---

### Post by Pnp1434 on 2007-05-15
yes it was a live CD. I in fact had lot trouble getting it to boot from the CD itself. And whenever I did manage to boot, when I try to install, would stall at 90% when it says 'detecting hardware'. I had no such installation issues with Ubuntu studio but its not starting!

---

### Post by Gmbrdilos on 2007-05-15
could be a hard drive problem. I had an issue like this on an old computer I tried to convert. Turned out the hard drive was damaged.
Did the previous operating system run smoothly?

---

### Post by Pnp1434 on 2007-05-15
Yes no issues with dual booting XP which I currently have. In fact I ran the diagonics to check for the errors on the hard disk sometime back and it turned out to be ok. Also I managed to install and run Suse 10.2, Madriva and PClinuxOS successfully when I tried them out recently. I have problems in installing only with Ubuntu!

---

### Post by Gmbrdilos on 2007-05-15
check the CD for errors that could cause problems too.

---

### Post by Pnp1434 on 2007-05-15
I did that as well and seems to be fine.

---

### Post by Gmbrdilos on 2007-05-15
then I have no idea mate, I am pretty new to ubuntu myself
I didn't install a clean copy of studio though, installed fiesty first, then upgraded when studio came out.

---

### Post by bodhi.zazen on 2007-05-16
I presume the problem is that you need a driver for your nvidia card.

When it boots to a black screen, can you get to a terminal ?

Hit Ctrl-Alt-F1 and see if you get a text log in. If so we can install the nvidia drivers from the command line.

---

### Post by Pnp1434 on 2007-05-16
Thanks I checked it by trying to boot without splash. It gave a message which read something like this " unable to load or locate xx43 microcode" and then in the next line it read it said 'starting gnome display manager....' and it stalls!. I vaguely remember the similar problem i face previously as well that convinces me that this has to to with the display card. Can you please help me out in configuring it?

Thanks
Pnp1434

---

### Post by PapaSmirf on 2007-05-19
The problem is a lack of a Nvidia driver.  Just do the following:

When you get the black screen of death, hit control, alt, F1 to get to the command line and login.

Then type:

sudo apt-get install nvidia-glx nvidia-kernel-common

It may ask you to insert the Ubuntu CD/DVD.

Now, update the xorg.conf file by typing the following:

sudo nvidia-xconfig

Now just type:

sudo reboot and you should be fine.

---

### Post by sornen on 2007-05-19
You need to install this module:
 
linux-restricted-modules-2.6.20-15-lowlatency

---

