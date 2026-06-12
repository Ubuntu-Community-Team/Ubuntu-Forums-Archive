---
title: "Resolution problem w/ ViewSonic"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by New User on 2007-02-10
How can I set the resolution on my widescreen monitor? I tried changing the xorg.conf file myself by finding bits of info. on the internet but just ended up crashing the system. I also have no clue as to the Linux lingo so I get hopelessly lost in any forum that talks about code.

This is my first time to Linux. It's my first day to be exact. I have an older HP computer that I wanted to use Ubuntu 6.10.

HP Pavilion 775y

Monitor - ViewSonic VX2025wm
GFX Card - nVidia Geforce Ti 4200

Other Hardware
Processor - Intel P4 2.8Ghz
Motherboard - MSI MS-6577 ver2.1
Sound - Soundblaster Live! 24bit
Intel chipset

---

### Post by Matt Yun on 2007-02-10
Have you tried using the Screen Resolution tool (System menu -> Preferences)?  You want 1650x1080 @ 60Hz for that monitor.

---

### Post by New User on 2007-02-10
Yes, but the resolution preferences only go as high as 1024x768. There is no selection to set the resolution higher.

---

### Post by xtrumanx on 2007-02-11
Having the same problem here, I'm using a 9600xt and it perfectly capable of running at 1280x1024 (so is my monitor) but System --> Resolution only goes as far up as 1024x768. this used to happen with my windows as well up until i installed my ati driver. could it be that i need to install the ati driver 1st? or would a few changes to the system allow me to access higher resolutions?

---

### Post by xtrumanx on 2007-02-11
i fixed my problem. here's the link i used for instructions:

[http://ubuntuforums.org/showthread.php?t=269052&highlight=1280](http://ubuntuforums.org/showthread.php?t=269052&highlight=1280)

I personally manually edited the xorg.conf file. More specifically the Screen section (Section 3b on the above link). Then i restart my system wit Ctrl+Alt+Backspace and it loaded it up on my wanted resolution. Hope it work for you :) 

P.S. remember to make backups just in case

---

### Post by Matt Yun on 2007-02-11
Then open a console and do the following:

$ sudo dpkg-reconfigure xserver-xorg

This will allow your system to redetect the hardware and reconstruct your xorg.conf

** Edit **

Oops, didn't refresh the page; congratulations on fixing the problem.

---

### Post by New User on 2007-02-19
Got it working!!!!

Many thanks to everyone!

Here is so more usefull info that also helped me.

[http://ubuntuforums.org/showthread.php?p=1597740](http://ubuntuforums.org/showthread.php?p=1597740)

---

