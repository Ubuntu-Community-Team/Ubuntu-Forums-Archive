---
title: "[SOLVED] Change Resolution in PSUbuntu (PS3)"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by tomihasa on 2008-01-26
I installed Ubuntu 7.10 to my PS3. How do I change the screen resolution? There doesn't seem to be a place where I could make any system settings. My HD TV is LG 32LT75.

---

### Post by overdrank on 2008-01-26
> **tomihasa said:**
> I installed Ubuntu 7.10 to my PS3. How do I change the screen resolution? There doesn't seem to be a place where I could make any system settings. My HD TV is LG 32LT75.

HI and welcome, have you tried under system, preference, screen resolution. :KS

---

### Post by tomihasa on 2008-01-26
> **overdrank said:**
> HI and welcome, have you tried under system, preference, screen resolution. :KS

That's my problem. When I click System on top, an installation program for Evolution starts, but the installation window is so big I need to close it. The low screen resolution seems to make it difficult to do anything with Ubuntu so that the system might function "abnormally" or something when trying to use the mouse to point at something. Can I manually change the screen resolution before I start the graphical user interface?

---

### Post by nedrige on 2008-01-27
Holding down the Alt key will let allow you drag the window.

---

### Post by nedrige on 2008-01-27
Typed that really fast  - :-) .

---

### Post by tomihasa on 2008-01-27
I found a way to get to the System menu: I click Applications (or Places), I use keyboard to go to System and then Settings (or similar, I have the Finnish version of Ubuntu), but on the Screen Resolution Preferences window I have only one option:

*Resolution: 576x460.*

How do I add more resolution options there? Can I manually change a Linux settings file? What should I add there? My HD TV has 1080p, HDMI.

---

### Post by tomihasa on 2008-01-27
I found some interesting pages:

[http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/](http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/)
[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)
[http://www.edepot.com/playstation3.html](http://www.edepot.com/playstation3.html)

Now my menus are gone, because the screen area is too big for my HD TV, but things are getting better as I now have a bigger resolution!

---

### Post by tomihasa on 2008-01-29
Problem solved. I started nano:

```

sudo nano /etc/kboot.conf

```

And edited kboot.conf (The end of the UUID part is hidden, just in case.) (First I used video=ps3fb:mode:133 for Fullscreen 1080p, but the menus, trash bin, etc. disappeared, so I switched the number 133 to 5.):

```

message=/etc/kboot.msg
default=linux 
timeout=100 
root=/dev/sda3 
linux="/boot/vmlinux initrd=/boot/initrd.img video=ps3fb:mode:5 root=UUID-..."

```

I started nano again:

```

sudo nano /etc/X11/xorg.conf

```

And edited xorg.conf:

```

Section "Screen" 
   Identifier      "Default Screen" 
   Device   "Tyypillinen näytönohjain"
   Monitor   "Tyypillinen näyttö"
   DefaultDepth    24 
   DefaultFbBPP    32 
   SubSection "Display" 
           Depth           24 
           FbBPP           32 
   EndSubSection 
   SubSection "Display" 
           Depth           15 
           Modes           "1024x720" "1024x768" "800x600" "640x480" 
   EndSubSection 
   SubSection "Display" 
           Depth           16 
           Modes           "576x384" "1024x768" "800x600" "640x480" 
   EndSubSection 
EndSection 

```

That file contains a bit Finnish as I installed the Finnish language version. Some approximate translations:

"Tyypillinen näytönohjain" = "Generic Video Card"
"Tyypillinen näyttö" = "Generic Monitor"

---

