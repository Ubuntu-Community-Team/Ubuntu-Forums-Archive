---
title: "3D graphics question."
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by iconfly on 2007-03-17
Hi, I have installed Ubuntu and am very pleased so far. Been doing things like audio streaming and other stuff that I never bothered with in Windows.

I am confused regarding 3D graphics and what I should expect.

My system works fine.  However I installed Google Earth and when launched it makes the CPU hit 100% and freezes the computer.

I suspect my graphics card has not installed correctly, but do not know how to prove that.  It is a  ATI all-in-wonder 9800 with 128 megs of memory.

When I looked at the device manager, it said nothing about graphics.

How do I find the correct driver and load it?  How do I find out what it is running at the moment?

Thanks in advance. Jimmy.

---

### Post by peabody on 2007-03-17
If you know how to launch the terminal program, try copying and pasting this command into it and hitting enter:

glxinfo | grep direct

If the result is "No" then you do need to install ATI's proprietary drivers.  I'll try and find a good howto link for those.

EDIT: Here's a HOWTO.  It describes an earlier version of the drivers, so be sure to get the latest version, but the instructions should be about the same. 

Ack! I forgot the URL: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

---

### Post by iconfly on 2007-03-17
Thanks for the super quick reply peabody, I tried that command and it said   no, so I guess I will have to load the correct driver.

I come across this site. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I have downloaded the program which detects and install ATI and Nvidea drivers.

Going to give it a go, if it works I will be well impressed!!!

Will post when done.  Thanks.

---

### Post by iconfly on 2007-03-17
Well unfortunately,  Envy did not work.

getting late for me, so I will go though your how-to tomorrow and give that a try.

Will post reply when done, thanks!!

---

### Post by BarfBag on 2007-03-17
I helped a friend load the correct drivers for his ATI card.  We used [this]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") howto.  It worked without a problem.

---

### Post by iconfly on 2007-03-18
Cheers Barf. The problem I find is the variety of models. Mine is a ATI all_in_wonder
9600 se, which I gather is a cut down version of the 8600 Pro !!!


All very confusing, but I will give it another go. Not even sure if I need full blown 3D graphics for the stuff I run.

---

### Post by mcduck on 2007-03-18
Just run these commands, they should be all that you need to get your 3D acceleration working:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

---

### Post by iconfly on 2007-03-18
I tried that McDuck, still no joy, seems everything is in place but something is not loading properly ?????

jim@jim-desktop:~$ sudo apt-get install xorg-driver-fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

jim@jim-desktop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
jim@jim-desktop:~$ 


But I still get;

jim@jim-desktop:~$ fglrxinfo 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

### Post by sad_iq on 2007-03-18
According to this site ( [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) )it says you also have to run **sudo apt-get install linux-restricted-modules-$(uname -r)** and after     sudo aticonfig --initial run **sudo aticonfig --overlay-type=Xv** ...just make sure you follow everything right.
 Also take a look at the troubleshooting page at: [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

---

### Post by iconfly on 2007-03-18
Thanks to all who helped.

I've cracked it!!!!  I re-ran  'Envy'  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) from this site, and all is well!

I can now run Google Earth !!!!

Many thanks to you all and  Albert!!!

Envy is worth a try for anyone having graphic card problems.

---

### Post by iconfly on 2007-03-18
Just an update,  Google Earth is absolutely buzzin' along now.


Thanks to all!!!!!!

---

