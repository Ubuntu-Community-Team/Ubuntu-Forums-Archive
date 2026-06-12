---
title: "Black Bar At Left of Screen"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by lark on 2006-06-03
Hi everyone!

I installed Dapper Drake, but I am having a small problem.  There is a half-inch black bar on the left side of my screen.

I scoured the forums, and then tried going to the nVidia website and downloading the driver in linux form (it is a .run file) to the Desktop and then typing "sudo sh" with the package name.

I get a message like "ld not found, please make sure it is in your path if it is installed".  I am 100% a newbie, but I really want to learn, so if someone could tell me what to do and why, I would be really grateful!

Edit, it says exactly, "Unable to find the system utility ld; please make sure you have the package "binutils" installed.  If you do have binutils installed, then please check that led is in your PATH."

---

### Post by OPaul on 2006-06-03
Usually the black bar is on the right side, so this may be a different issue, but try following Note #7 in this guide.
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#NOTES_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#NOTES_SECTION)

This guide will also tell you how to get your Nvidia driver up and running.

---

### Post by meng on 2006-06-03
I was under the impression that
sudo apt-get install nvidia-glx

would set you up with the latest nvidia drivers. Seemed to work for me at any rate.

The other issue is - I don't mean to be insulting here - but the black bar can't be reduced by fiddling with your monitor settings at all, can it?

---

### Post by lark on 2006-06-03
Thank you both for the responses!  I checked the document but it was, ah, kind of confusing me.  So I tried your suggestion, meng, (the sudo install thing) and it installed properly (yay!), but I still can't make the driver I downloaded install?    When you say fiddle with the monitor, do you mean the horizontal button on the front of the screen or something more complicated?

I have this horrible feeling I'm being a complete dunce here!  I'm not usually so stupid, but I sure feel like I'm floundering.  I'm going to try to read over the doc.gwos.org document and see if I can pick up some basic techniques, too.

UPDATE!  I fiddled with the button on the front of the monitor until everything looked wide enough and centered.  I will wear the dunce hat until midnight!  Thanks again for the help!

---

### Post by meng on 2006-06-04
Oh as I understand it, if nvidia-glx is installed, you don't need to install the binaries from nvidia, it's already done. You can start NVIDIA settings from GNOME (alt-f2 and then nvidia-settings, or otherwise it may be in the menu, probably Applications > System Tools) and this program will tell you what version drivers are installed (probably 1.0-8762) and a whole lot of other stuff.

And, yes, I mean adjusting "horizontal position" and/or "horizontal size" on the monitor.

If these don't work out for you, you may need to choose another screen resolution.

---

### Post by Raavea on 2006-06-04
Ah, I had the same problem at first when I installed Ubuntu 5.10, but it came naturally to me to fiddle with the buttons as I'm forever hitting the damn things by accident...

 I wonder why it happens?

---

