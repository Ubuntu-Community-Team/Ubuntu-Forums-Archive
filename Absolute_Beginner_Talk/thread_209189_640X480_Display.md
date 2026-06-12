---
title: "640X480 Display"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Heffy on 2006-07-04
I downloaded the Ubuntu today and am now running on the CD.  I want to install it but the screen resolution is set on 640X480 and there is no other options for different sizes.  Because of this I can see the total screens for making choices for instaling.  Can move the screens to see any buttons either.

Heffy

---

### Post by halfvolle melk on 2006-07-04
Hi,

**Either** click: applications -> accessories -> terminal
**Or**, if the above is outside your screen, press: CTRL+ALT+F2

Then type "sudo dpkg-reconfigure xserver-xorg". Choose all the defaults (by pressing enter) untill you get to select your screen resolution. Press spacebar to select the desired resolution. Choose more defaults until asked to choose from "simple", "medium" and "advanced". Select simple unless you know what you're doing. Press enter some more. Reboot.

That might fix it.

---

### Post by Heffy on 2006-07-04
Well it looks like I can't set the resolution other than 640X480.  Also after messing with the option to move the screen to go through the install process it locks up when scanning for partition work.  It did that twice, so I guess I'll have to stick with Windows. :(

---

### Post by halfvolle melk on 2006-07-04
"sudo dpkg-reconfigure xserver-xorg". Choose all the defaults (by pressing enter) untill you get to select your screen resolution. Press spacebar to select the desired resolution"

Did you do this? Add 1024x78? to the list? What kind of video card do you have?

Or, if the graph. install fails for you, you could try the "Alternate install CD"
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)
It's somewhere near the bottom, just before the actual downloads.

---

### Post by Heffy on 2006-07-05
I downloaded and installed the "Alternate install CD" and got it installed, and the resolution changed.  Thanks for your help!

Heffy

---

### Post by DavidJE13 on 2006-07-18
I'm having this exact same problem on an old computer of mine. I guess it's better to mention it here than start a new thread.

I would rather not download the Alternate Install CD, since every time I've downloaded an image and writen it to a disk, it's turned out to be damaged (no, I'm not writing it to the disk as a file :P I think it's a fault in my CD RW, or that I'm buying cheap CDs :D)

I can cope with the resolution by moving the window around as needed for each stage, but the partitioner is causing a problem. Is there any way to install *using the live CD* that doesn't open the partitioner?

---

### Post by muep on 2006-07-18
DavidJE13, have you done the dpkg-reconfigure thing? If you can't get display to work in the livecd, getting it correct in the installed Ubuntu is going to be hard.

I think you can drag windows around with the mouse by holding alt down.

Anyway, most hardware starts to work ok with good resolutions after a reconfiguration.

---

### Post by DavidJE13 on 2006-07-18
No, I haven't tried using dpkg-reconfigure yet, though since it seemed to work for Heffy I'm guessing it will work for me too. I'll try it later (some time tommorow) and see what happens.

btw, I'm using right-click -> Drag in the application bar to move the window around. The alt thing could be useful though, thanks

---

### Post by muep on 2006-07-18
Remember, if it doesn't work the first time, try again. It is safe on the livecd.

If it doesn't work, the problem is probably in monitor settings.

---

### Post by Ragazzo on 2006-07-18
After "sudo dpgk-reconfigure xserver-xorg" press ctrl+alt+backspace to restart the GUI.

---

### Post by Jax Kovak on 2006-07-19
If none of that works you can always try this:

[http://www.ubuntuforums.org/showthread.php?p=1222707#post1222707]("http://www.ubuntuforums.org/showthread.php?p=1222707#post1222707")

It hasn't worked for everyone but it worked like a charm for me.

Jaz

---

