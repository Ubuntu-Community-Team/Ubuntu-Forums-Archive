---
title: "Puzzled by ATI Radeon X700"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-21
After fresh install from alternate x64 Feisty CD, Ubuntu boots into a black screen with my ATI Radeon X700.

I thought I knew the answer:


1- check restricted repos in /etc/apt/sources.list are enabled via nano

2- edit /etc/X11/xorg.conf to include:
```

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

```3- sudo apt-get update

4- sudo apt-get install linux-restricted-modules-$(uname -r)

5- sudo apt-get install xorg-driver-fglrx

6- sudo depmod -a

7- sudo aticonfig --initial

8- sudo aticonfig --overlay-type=Xv

9- startx, desktop comes up, prompts to enable the proprietary ati driver, agree

10- reboot. goes to black screen. so reboot into recovery mode

11- dpkg-reconfigure xserver-xorg, try fglrx driver instead of ati
(fglrx driver works after a quick meddle with the refresh rate)

12- reboot, same prob, black screen.

13- try again with 'radeon' as the driver specified in xorg.conf, same prob.



Seems that I can use any of the drivers 'ati', 'fglrx' or 'radeon' and they all run perfectly, so long as I start them manually from recovery mode via "startx".


None will load the GUI by themselves on a normal startup though.


Weird thing is, I've had this card running just fine using a Feisty install off the same CD, on the same computer, twice recently.. just can't seem to crack it this time. Unfortunately the last two times I managed to get it working, I was really, really new at Linux, my head was completely fried, and I didn't take comprehensible notes.


Does anyone have any suggestions... ?


oooh.. hang on..
[http://ubuntuforums.org/showthread.php?p=2890370#post2890370](http://ubuntuforums.org/showthread.php?p=2890370#post2890370)

---

