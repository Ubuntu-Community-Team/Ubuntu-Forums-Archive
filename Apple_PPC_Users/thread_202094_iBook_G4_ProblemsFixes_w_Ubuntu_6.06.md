---
title: "***iBook G4 Problems/Fixes? w/ Ubuntu 6.06***"
date: 2006-06-22
forum: Apple PPC Users
---

### Post by zachws on 2006-06-22
This is for the growing iBook G4 Ubuntu community. 

Common problems:

Slow Mouse
No Wireless (Airport Extreme)
No Bluetooth
No 3D Acceleration (ATI, don't know about Nvidia)

Please post problems you have and we can all try and find a fix.:-\"

---

### Post by wingk1314 on 2006-06-24
XGL+Compiz doesn't work as far as i know
and yeh.. the trackpad is annoying too
these are the 2 things keeping me from using ubuntu atm.. I'll wait til there's proper drivers out for the G4 ibook before I start using ubuntu

---

### Post by rshd301 on 2006-06-25
[QUOTE=wingk1314]and yeh.. the trackpad is annoying too[/QUOTE]

I got a workaround for the problem from someone on the forum. The link below takes you to a Gentoo site where there are details of how to determine the type of touchpad you have and what config settings need to be made in xorg. It certainly is working for me-

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

I did the -
cat /proc/bus/input/devices
This showed me I had a Synaptics touchpad

I then did -
sudo gedit /etc/X11/xorg.conf
When opened, I saved it as xorg.conf.old (just in case) and cut and pasted the extract from the Gentoo site into the appropriate place in xorg. Some of the speed settings at the bottom need raising (I found) but after restarting X, the touchpad is definately useable.

---

### Post by keyshawn on 2006-06-29
This is a semi-unrelated note, but:

There's a fix for this bug, [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)
(which made my attempt to use the live 6.06 on my ibook G4 impossible) but have the desktop CD's been updated to reflect this change ? 

I looked on a couple mirrors, and both of them have the desktop cd's released on June 1st, I thought the development team would have released new cd's (for ppc) that would have fixed this critical bug. 

So, did anyone else here run into this problem ? How did you get around it ?

Thanks,
keyshawn

---

### Post by poseidon21190 on 2008-02-18
hi i just installed Ubuntu 6.06 on my moms ibook G4 and she wants to be able to use flash so she can see youtube videos, ive been looking all over the internet to try to find a solution to this problem and i cant i really need help on this.

---

