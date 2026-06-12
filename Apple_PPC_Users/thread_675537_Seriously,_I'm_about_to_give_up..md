---
title: "Seriously, I'm about to give up."
date: 2008-01-22
forum: Apple PPC Users
---

### Post by Lupin the 3rd on 2008-01-22
I have a iBook G3. The non-clamshell version (or w/e) and I've been trying to install Ubuntu it for about six months now.  Like I've stated in my previous posts when I boot the Live CD and come to the desktop the right side of my screen (about 2 inches) is totally black from bottom to top. The bottom inch is the exact same thing as the top. Like an exact copy, i.e. when I put my cursor at the top it show it at the bottom as well as the top. I've thrown in the book on my side and now I guess it's up to you to try to make sence of this. Thanks in advance and I would appreciate any feedback even if it isn't the news I hope for.

---

### Post by CheShA on 2008-01-22
I've tried to install various flavours of Linux on my iMac G5 over and over again, over the course of like, 2 years and I can confirm that Mac PowerPC support is fairly sketchy - it works great for many Macs, but some others (like the very specific production run of my iMac) are not supported at all and probably never will be.  If you want to give "Linux" a go and not specifically Ubuntu, try Yellow Dog Linux (special Mac specific Red Hat derivative with a Mac centric community). If that doesn't work,  then I'd say your chances of getting Linux on your G3 are out.

Edit: I just remembered: If there's a way to edit the boot options you might try adding "video=ofonly" to the command that the boot loader executes.

---

### Post by stream303 on 2008-01-22
Don't give up!

I don't know what version of Ubuntu you are trying to install.  May I suggest the "alternate" text based installer of Feisty 7.04 for that machine?  Frankly, I always use the alternate installers, burn with the slowest speed possible, and use high-quality cd media.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

It sounds like you are close.  The alternate install cd is not live and may take you much further.  Once we get you up and running we can go from there.

Keep this handy:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Give this a shot and let us know.

---

### Post by GVCarroll on 2008-01-22
> **Lupin the 3rd said:**
> Like I've stated in my previous posts when I boot the Live CD and come to the desktop the right side of my screen (about 2 inches) is totally black from bottom to top. The bottom inch is the exact same thing as the top. Like an exact copy, i.e. when I put my cursor at the top it show it at the bottom as well as the top.

I have this problem installing 7.04 Feisty on the same machine (white G3 iBook 500MHz). It will install.

This is a goof with a configuration file for the monitor (a goof as far as PPC iBook graphics cards are concerned anyway), which is telling it to use an 800x600 screen instead of 1024x768. It's just tiling the screen and wrapping around the edges, like tiling a small desktop picture.

It's not possible to fix it on the LiveCD because it requires editing the config file and restarting which you can't do on a CD because you can't write to a burned CD obviously, but you CAN FIX THIS after it's installed.

Boot the LiveCD, when it's done booting, right click on the panel at the top, go to Properties, and choose AutoHide. Do the same with the bottom panel. You need to do this because the installer window is very tall, and you need to be able to click the default orange highlighted Next/Okay button at the bottom right corner of the installer window, which you can't do unless you hide the panels for that little bit of extra screen real estate.

Launch the installer and do your install.

When you're done, and have restarted, you're still going to have to fix the screen weirdness.

What you need to do is edit the xorg.conf file that resides in /etc/X11/

Check this out for a working xorg.conf for your machine:

[http://ubuntuforums.org/showthread.php?p=3227440#post3227440](http://ubuntuforums.org/showthread.php?p=3227440#post3227440)

Follow the instructions there, do a restart, and you should be good to go.
You'll probably get a notice to install a TON of updates (if it's Feisty) which you should do (it takes awhile), then you're set.

---

### Post by Midwest-Linux on 2008-01-23
I also recommend the alternate text installer. I have installed Ubuntu 7.04 in two I-Macs and one G-3 B&W and only used the text based installer in every case.


How much RAM do you have in the machine? On one of my I -Macs, it is the older version that uses SO-Dimms (same as a laptop PC uses for older SO-Dimm PC100 types) I can use the machine with its 192MB but its slow. Ubuntu 7.04 really needs at least 256 MB to run just OK. If there is low RAM on the machine, try Xubuntu and/or upgrading the RAM. Whatever you do or use...use the text based installer.

---

### Post by Lupin the 3rd on 2008-01-23
How do I right click?

And it has 576 mb Ram

---

### Post by Ripfox on 2008-01-23
Usb mouse

---

### Post by Lupin the 3rd on 2008-01-23
I figured it out, for some reason when I press the eject key it right clicks.

---

