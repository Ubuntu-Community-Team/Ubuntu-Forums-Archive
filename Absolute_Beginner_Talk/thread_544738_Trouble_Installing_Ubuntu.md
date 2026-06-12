---
title: "Trouble Installing Ubuntu"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by finjetsu on 2007-09-06
Ok im new to Linux, and trying to install Ubuntu off the live CD,

however i got the /bin/sh: can't access tty; job control turned off problem and followed the solution in this thread [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

this took me past the command prompt stage but then i get a message saying it has failed to start the X Server(your graphical interface)

it takes me to a diagnosis screen

X Window System Version 7.2.0
Release Date: 22 January 2007
X Potocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007 etc...

it mentions to check [http://wiki.x.org/](http://wiki.x.org/) to see if my version is upto date, which it isn't, could this be the problem?

any help is greatly appreciated.

---

### Post by p_quarles on 2007-09-06
No, you don't need to update X. The problem more likely has to do with your graphics card. What type of card do you have?

What you'll most likely have to do is use the "alternate" installation CD, and then install and configure the graphics card driver once the system is installed.

---

### Post by finjetsu on 2007-09-06
ah i see, i have a NVIDIA GeForce Go 8400M 

and what do you mean by "alternate" installation CD, i take it's another version i have to download sort of thing?

edit: found the alternate installation CD am downloading now

---

### Post by yabbadabbadont on 2007-09-06
Yes, it is a different version of the installation disc.  You can get it [here.](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fubuntu.mirrors.tds.net%2Fpub%2Freleases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=&alternatecd=alternate)
(Note, that is from a US mirror.)

---

### Post by WebSiteGuru on 2007-09-06
> **finjetsu said:**
> 
and what do you mean by "alternate" installation CD, i take it's another version i have to download sort of thing?


Text base installation :D

---

### Post by finjetsu on 2007-09-06
> **WebSiteGuru said:**
> Text base installation :D

sounds fun :D................. :(

---

### Post by p_quarles on 2007-09-06
And once you've got that running, you'll need to install the driver for the graphics card. The following link has some resources that should help with that:

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by finjetsu on 2007-09-06
ah wicked cheers for your help :D

---

### Post by finjetsu on 2007-09-07
more troubles,

ok i followed the installation process on the alternate cd, and installed ubuntu, it reboot at the end, then when i loaded ubuntu i get the xserver.

then it says this
starting up ...
[00.24 3571] PCI: Failed to allocate mem resource # 6:20000@e0000000 for 0000:0 1:00.0
loading please wait ...
kinit: name_to_dev_t (/dev/sda5) = sda5(8,5)
kinit: trying to resome from /dev/sda5
kinit: No resume image, doing normal boot.
Ubuntu 7.04 tty1
Ubunutu login

when i log in i get the command line,

however i rebooted it as i dint know where to go from here, and now the laptop won't even boot up, the fans start spinning and you can hear the HDD for a few seconds but then it all stops, nothing comes up on the screen either.

any help is greatly appreicated

---

### Post by p_quarles on 2007-09-07
So it won't start at all? Can you even get to the BIOS interface?

The post I linked to above has a program called Envy that will automate the installation of your graphics driver. If you can get back to the command line, you'll be able to use that to run Envy [[link]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")]

But if it won't do anything, I wouldn't know what to tell you. Other than to take it to a repair shop.

---

### Post by finjetsu on 2007-09-07
nah doesn't even get into bios, its really weird, am getting a replacement on monday, luckily i only got it yesterday so its still under its warrenty.

---

### Post by p_quarles on 2007-09-07
Good. Sounds like it was a hardware problem anyway, Hope you have better luck with the replacement. :)

---

