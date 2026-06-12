---
title: "Dual Display with X800GT troubles..."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Ade_Grub on 2007-08-12
G'day guys,

I'm quite new to Ubuntu (and Linux for that matter) and I love it thus far. The only issue I am having is trying to set up my dual monitors with my ATI X800GT graphics card. I've searched the web for various tutorials but as yet none have seemed to work. I went through the wiki 'how to' and fiddled with my xorg driver but that ended disastrously with Ubuntu booting up to the shell. I managed to roll back my old configuration so all is well but I am back to where I started! I have the fglrx driver and two LCDs. One is hooked up via VGA and the other DVI. I noticed that one shows up in the xorg driver with the CRT prefix. Is this because its hooked up via VGA? I've heard the x800 cards are quite hard to configure when dealing with dual display setups so any help would be greatly appreciated.

Cheers.

P.S. Please help me in my quest to ditch Windows! Yay!

---

### Post by DjBones on 2007-08-12
Use envy to install the ati driver then use this thread to install big-desktop:
[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)
the "step 2" is all that i needed to do lol

((also, the CRT/LCD part shouldn't make a difference aside from the refresh rate, both of my LCD's seemed to work))

---

### Post by Ade_Grub on 2007-08-13
Thanks for you're reply DjBones.

Unfortunately I ended up with the same result. As soon as I get to step 4 of the 'how to', everything gets rest to 640x480 resolution!

sudo aticonfig --query-monitor

  Connected monitors: crt1, tmds1
  Enabled monitors: crt1, tmds1

sudo aticonfig --enable-monitor=crt1,tmds1

After that last command my monitors reset to 640x480 and are still mirrored :(

Any other suggestions?

---

### Post by Ade_Grub on 2007-08-13
Alrighty! I've made some ground. I didn't realise that typing the commands in at the terminal was not enough to enable big desktop on its own.

So I went to Applications -> Accessories -> ATI Catalyst Control Center (which is installed when installing the ATI driver with 'Envy' and then enabled big desktop in the drop down. This successfully enabled big desktop but one of the monitors (the one that hooked up via VGA) is at a lower resolution. The resolution in Catalyst in 2560x1024 (so each monitor at 1280x1024). While the DVI LCD looks to be at this resolution the VGA LCD looks to be at 1024x768. When I put my mouse onto the border of the screen the whole actual screen scrolls to accommodate the unseen real estate.

Bugger! I'm so close.

---

