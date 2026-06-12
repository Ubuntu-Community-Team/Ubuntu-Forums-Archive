---
title: "Horizontal lines glitches when playing video (Ubuntu 7.04, Nvidia)"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by SGTEdwards on 2007-06-09
I recently Installed  Ubuntu 7.04 on my computer  (got tired of Win XP  :rolleyes:)

The problem starts when I'm  playing video (avi,mkv,ogm,DVD) on Totem or VideoLan, on some scenes I can see horizontal lines glitches messing around (specially on high motion :sad: ), I didn't have the chance to see if it happens also on PC games since I haven't installed any yet, but I can assume that I will get the same problem.

After looking this issue and google search I dint get any concrete results, I only managed to return my monitor (HP Pavilion M70) refresh rate to its Optimal capabilities 1024 x 768 @ 85Hz (compared to 50/60Hz before) on the Xorg.conf, but still  see the lines.  

I can conclude the horizontal synch its not working properly on Ubuntu.

Any help to fix this horizontal glitch would gladly appreciate it.

Here's information about my PC:
OS: Ubuntu 7.04/ Win XP(Virtualbox Guest) x86
Processor: Intel Celeron 900 Mhz
Ram: 512 MB
Video Card: XFX NvidiaGforce 4 MX 4000 PCI 64MB
Video Card Driver: 1.0-9631 (the card doesn't like the latest one, hmm)

Thank you

---

### Post by Joakim Stokland on 2007-08-30
Hi! Have you fixed your problem yet?
This thread helped me with the exact same problem (I've got Intel chipset too):
[http://ubuntuforums.org/showthread.php?t=123522](http://ubuntuforums.org/showthread.php?t=123522)
I am using VLC player and Xine. Try one of the filters in Video -> Deinterlace (start a movie first to access the menu), and you'll most likely get rid of the glitches.

Joakim

---

