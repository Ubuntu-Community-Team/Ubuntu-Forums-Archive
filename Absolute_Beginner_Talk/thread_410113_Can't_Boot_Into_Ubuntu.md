---
title: "Can't Boot Into Ubuntu"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-04-15
Hi, I have a Dell Inspiron E1405 laptop and when I try to boot to Ubuntu Live CD this appears


Start or install ubuntu
start in safe graphics mode
etc.


When I try either of those top two, this set of errors occurs:

Quote:
Failed to start the X server (your graphical interface)
It is more likely that it is not set up correctly. Would you like to view the X server to diagnose the problem. [17178756.068000]bcm43xx:Error:microcode
"bcm43xx_microcode5.fw" not available or load failed.
<Yes> <No>

When I click yes this shows up
Error:Microcode "bcm43xx_microcode5.fw" not
available or load failed. Version 7.11
Release date: 12 May 2006
Protocol version 11, Revision 0, Release 7.11.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build date: 07 July 2006
or load failed. reporting problems, check [www.wiki.x.org](www.wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log File:/var/log/Xorg.0.log time: Mon Apr 2 19:24:36 2007
(==) Using config file: "/etc/X11?xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1)
found
(EE) I810 (0): No video BIOS modes for chosen depth.
(EE) Screen(s) found , but none have a usable configuration.
Fatal server error:
no screens found
This is a blue and white and red screen with lots of weird letters around that.

Then a black screen pops up:
firmware_helper [4970]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
for device '/class/firmware/000:0c:00.0' with driver 'bcm43xx'
[17179669.95200]bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available
error load failed.
From the research I've done, the bcm43xx is the wireless driver ubuntu is trying to use, but it's not compatible with the wireless on the Inspiron 1505. Is there a way to disable this check or do anything so I can actually finish the install, and then go back and fix the wireless driver?
Also, I tried to do sudo dpkg-reconfigure xserver-xorg. And it takes me to the options, but I have no idea what type my screen is. Could anyone fix this problem? THanks!:guitar:

---

### Post by mojo123 on 2007-04-15
what speed did you burn the disk at, try slower speeds

---

### Post by mikecomua on 2007-04-15
I didn't burn it I bought and it's a gamer's edition dvd.

---

### Post by NicoleM on 2007-04-15
i'm not sure how much i can help, but failing to load X is usually a video card/driver issue from what i understand.  if you posted your video card it might be helpful for others to identify your problem.

i had the same error message when initially booting from the livecd because it was detecting my on-board video rather than the PCI card i had installed even though the on board graphics were disabled in the bios.  

i had to manually find the busID for my video card using the lspci command then edit the /etc/X11/xorg.conf file to detect that BUSID and also tell it what driver to use.

i'd go into more detail, but I'm not sure it would be very helpful to you since the root of your problem is still undetermined.  

I still have to go through this each time I boot a livecd so I'm unsure whether this is a bug that has to do with having an extra video card installed or if it's something unique to my system.  I can dig up the thread I posted in if you think it might help.

---

### Post by mikecomua on 2007-04-15
From as much as I know my Graphics card is Intel Graphics Media Accelerator 950

---

### Post by juantovarm on 2007-04-15
Live cd seems to be a bit problematical at times. Try downloading the alternate install cd, burn the image at 4x and install it in TEXT mode.

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by mikecomua on 2007-04-15
What is it?

---

### Post by juantovarm on 2007-04-15
The alternate install cd is the old fashioned way of installing linux systems. No pretty graphical interface, just something more rudimentary, similar to a DOS application, but with very easy steps to follow. I sent you the link, you can download the image and burn it. Te difference is that with the live cd you can test run the software, with the alternate cd, there is no such possibility. It just installs, no preview, but, it is a lot stronger than the live cd

---

### Post by mikecomua on 2007-04-15
Is there a way to get the CD

---

### Post by juantovarm on 2007-04-15
If you have no internet connection or you have a dialup one and you do NOT like waiting for many hours to download, then i suggest another distro, because Ubuntu needs to download packages from the internet to finish the installation process and to have connection with the repositories

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by mikewhatever on 2007-04-15
Here is the straight link to 6.10 alternate x86 from Ukrainian location [http://releases.ubuntu.org.ua/6.10/ubuntu-6.10-alternate-i386.iso](http://releases.ubuntu.org.ua/6.10/ubuntu-6.10-alternate-i386.iso)
If you want a different version, pick one from [http://releases.ubuntu.org.ua/](http://releases.ubuntu.org.ua/)
Here is a guide on how to use the CD [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

