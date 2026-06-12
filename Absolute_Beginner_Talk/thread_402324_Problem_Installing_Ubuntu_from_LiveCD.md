---
title: "Problem Installing Ubuntu from LiveCD"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Arcanex0r on 2007-04-05
I've never used Linux before and after trying Vista and seeing how inefficient it is, I decided to try Ubuntu.  I'm currently trying to install Fiesty Fawn on my Dell Laptop (Inspiron 1505).  I've put the CD in and rebooted.  The Ubuntu menu comes up.  If I choose "Start of install Ubuntu" or "Start Ubuntu in safe graphics mode" it does its thing until it gets to this point:

> Failed to start the X server (your graphical interface)
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

It continues to repeat that last Error message until I shut it off.

Now, from the research I've done, bcm43xx is the Wireless Card drives that Ubuntu is trying to use, but it's not compatible with the Dell card in this laptop.  Any tips for how to get past this point and finish booting/installing?

---

### Post by Bachstelze on 2007-04-05
The bcm43xx driver is not the problem here. What kind of video card does this laptop have ?

---

### Post by Arcanex0r on 2007-04-05
It's a 128mb  ATI , not sure what the exact model is.  I'll try to find it

---

### Post by Bachstelze on 2007-04-05
That could very well be the problems as Ati cards are known to have weak Linux support. Have you tried installing with an Alternate CD ?

---

### Post by Jeeverz on 2007-04-05
Hello, i also seem to have the same problem, but after it boots from the cd mine gets stuck at a black screen and a X as my mouse pointer ?


any suggestions ?

i have a Dell Inspiron 9400 

Intel Centrino Duo 2.00Ghz

ATI Radeon X1400 256mb

---

### Post by ramjet_1953 on 2007-04-05
As Hymn-to-Life asked, have you both tried using the alternate CD?

As you have ATI video cards, you are probably better-off using a non-graphical installer and then load the ATI driver after install.

Regards,
Roger :cool:

---

### Post by Jeeverz on 2007-04-05
id hate to break your heart by saying that i dont know what the 'alternate cd' is 

but i did try it on my desktop... and walla ! it worked .. so im just going to forget about installing it on my laptop and partition my desktop so i can install unbuntu on it ..

sorry for wasting your time

and if u dont mind, i have a question on wireless cards ? is there a list i cant find or drivers or somthin for my Linksys Wireless Adapter ?


Cheers 

Jeeverz

---

