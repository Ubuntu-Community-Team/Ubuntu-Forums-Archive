---
title: "Getting the OS to recognize 1680x1050 monitor"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by recursion on 2007-10-15
I just installed Ubuntu this afternoon, and everything seems to be working fine except for the annoying lack of resolution options higher than 1024x768. I recently bought a new 1680x1050 widescreen monitor, and the smaller resolution is making everything on the screen maddeningly squashed/pulled. 

Similar threads on this forum have lead me to believe that I need to download a program to allow me to make my resolution higher. If this is true, what program is this and where can I find it? The other threads were largely from the perspective of someone who already knows what they are doing --- that's not me! :-(

Just so you have a bigger picture of what I'm dealing with, my monitor is an LG 22" Flatron Wide.

Thanks,
Briana.

---

### Post by jdfreshwater on 2007-10-15
> sudo dpkg-reconfigure xserver-xorg

this program will allow you to write a new xorg config file and select a higher resolution.

It is already installed.

---

### Post by recursion on 2007-10-15
When I tried this, the following message was printed in the terminal and it did no more:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071015203958

The settings appeared not to take. What did I do wrong?

---

### Post by Gazneth on 2007-10-15
Using Gutsy, which is still a little buggy but worth it, you can set resolution in System - Preferences - Screen Resolution.  Gutsy picked up and configured my Gforce 8600GTS OC and a 22" Acer monitor. Do you have enough video memory to handle that resolution?

---

### Post by recursion on 2007-10-15
> **Gazneth said:**
> Using Gutsy, which is still a little buggy but worth it, you can set resolution in System - Preferences - Screen Resolution.  Gutsy picked up and configured my Gforce 8600GTS OC and a 22" Acer monitor. Do you have enough video memory to handle that resolution?

I don't plan on updating to the next version until it is a bit more stable --- do you know how to fix my current problem?

---

### Post by cnico88 on 2007-10-15
I have an Acer 22" with that resolution and Ubuntu recognized it right away. You can wait 3 more days to wait for the stable 7.10

---

### Post by skompier on 2007-10-15
Feisty didn't recognize my widescreen either and I never got it too. I followed every forum post...nada. It was only after I installed 7.10RC did my monitor get set correctly and even automatically. Gotta love Gutsy.

---

### Post by Gazneth on 2007-10-15
Do a ```
sudo dpkg-reconfigure xserver-xorg
``` In the monitor detection step choose either medium or advanced, can't remember which and be sure to manually select the resolution you need. Only medium or advanced will let you do that.

---

### Post by Frak on 2007-10-15
Whats your video/graphics card.

---

### Post by recursion on 2007-10-15
> **Frak said:**
> Whats your video/graphics card.

ATI Radeon X300 SE.

---

### Post by Keith_Beef on 2007-10-15
Have you read [this thread]("http://ubuntuforums.org/showthread.php?t=441076")?

Beef.

---

### Post by Gazneth on 2007-10-15
In my above post I forgot to add, boot to the recovery console,command line only no GUI. Then run the code, doing this from within the GUI can cause difficulties.

---

