---
title: "screen size problems"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by njmacrai on 2007-10-11
Hello, My new LINUX operating system seems too big for my screen. I have a standard 17 inch monitor, but everything overlaps that and I end up having to bring in borders,etc. I have gone into the Monitor Settings and found a decent size, but it always reverts back to the big size. Any suggestions? I am using Feisty Fawn with an ATI Rage 128 video card (Kubuntu 7.04)

---

### Post by bigken on 2007-10-11
try this in a terminal sudo dpkg-reconfigure -phigh xserver-xorg

use this to select ati drivers and the correct resolution size for your monitor 
use the space bar to select the resolutions

---

### Post by njmacrai on 2007-10-13
Thank-you for your suggestion. It seems to work but only to a certain extent, then reverts back to the old "big screen" after I restart. The terminal command takes me to the ATI choice screen. That's all good. Then I understand how to use the spacebar to leave a star on the resolution that I want, but after I press ENTER it gives me a warning of "xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071013094901".......;which I don't really understand. Anyway, nothing seems to change at that moment so I have both restarted my computer as well as simply logout, but I always return to the "big screen". By the way, I have also gone into my actual monitors control panels where you press those buttons at the bottom of your monitor (like a TV set), but even that seems to have a minimal effect. What do you think? Its very kind of you to help.

Neil

---

### Post by njmacrai on 2007-10-14
Thank-you for your suggestion. It seems to work but only to a certain extent, then reverts back to the old "big screen" after I restart. The terminal command takes me to the ATI choice screen. That's all good. Then I understand how to use the spacebar to leave a star on the resolution that I want, but after I press ENTER it gives me a warning of "xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20071013094901".......;which I don't really understand. Anyway, nothing seems to change at that moment so I have both restarted my computer as well as simply logout, but I always return to the "big screen". By the way, I have also gone into my actual monitors control panels where you press those buttons at the bottom of your monitor (like a TV set), but even that seems to have a minimal effect. What do you think? Its very kind of you to help.

---

### Post by i-tech on 2007-10-14
can you attach the xorg.conf?

---

### Post by njmacrai on 2007-10-14
I don't think so. I copied and pasted that command but then something appears which includes "permission denied". Any other suggestions?

---

### Post by usarmykr on 2007-10-14
What driver do you use?  There is a script called Envy that will auto isntall nvidia/ati drivers from there website to your system.  Just google it, all you have to do once it installs is click next, everything is automated, and after reboot you get shiny new proprietary drivers complete with control panels.

---

### Post by ghost_ryder35 on 2007-10-14
> **njmacrai said:**
> I don't think so. I copied and pasted that command but then something appears which includes "permission denied". Any other suggestions?

do it as the root user

---

### Post by njmacrai on 2007-10-14
sorry, but what does "do it as the root user" mean?

---

### Post by bigken on 2007-10-14
type sudo infront of the command

---

