---
title: "[SOLVED] Owww start up in low graphics mode??"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-04-17
Morning everyone, hope life is wonderful wherever you are! 

Ok today so I boot up my 2 week old installation of gutsy gibbon, and instead of my usual boot, I see the Ubuntu symbol and progress meter for a few seconds, then a black screen showing 'checking anacron' and a few other things, then it stops at loading /etc/rc.local scripts (there are none) then a few seconds later a small graphic X and a dialog telling me the system is starting in low graphics mode. 

So we accept and I come to a desktop resolution of 600 x 800, Now I have for the last two weeks been successfully booting straight into my system, using the Nvidia Ge force 7 series card and restricted driver. I checked the restricted drivers manager and found that the NVidia restricted driver is installed and apparently in use. I have tried a few times this morning to re enable the correct driver through Administration > Screens and Graphics, but even after apparently accepting the changes on re boot the same thing occurs. 

I looked here for similar problems and found a little bit about the /etc/X11/xorg.config files, so decided to have a look at those and this is what I find (see attachment please). As you can see there appears to be a number of failsafe files numbered 1 thru 5 and a few config files 1 thru 3, so I am thinking that there is a problem in some setting resulting in multiple re writes of these files. 

Any ideas how I can restore my desktop back to using the Nvidia driver, and accelerated graphics, with 3d effects which I want?

---

### Post by bumanie on 2008-04-18
try > sudo dpkg-reconfigure xserver-xorg

---

### Post by canucked on 2008-04-18
I would also like to add that the new version of Ubuntu, 8.04 Hardy Heron, which will be released next week, has a nice feature if you choose Recovery in the GRUB boot menu.  It gives you an opportunity to repair your X-server without having to type in the terminal commands.

---

### Post by tropdoug on 2008-04-18
Thanks guys, will bve looking at the new release for sure. 

I did the  			 				sudo dpkg-reconfigure xserver-xorg but there were still some issues, I think because I had somehow installed both a generic and a i386 image at the same time, so I decided to reinstall from scratch and all is working well now. A bit of a pain, but a good learning episode. I like this OS

---

