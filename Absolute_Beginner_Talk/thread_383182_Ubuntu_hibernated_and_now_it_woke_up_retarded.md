---
title: "Ubuntu hibernated and now it woke up retarded"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by jrekkedal on 2007-03-13
I had my setup working perfectly, nvidia drivers actually installed correctly, software in without problems... then I made a simple but somewhat confusing mistake. I accidentally pressed the "Suspend/Hibernate" shortcut button on my keyboard and all hell broke loose.

First off, I saw the screen fade as if the screen saver was starting (which I saw flash for a second) and the PC went into hibernate.  Blinking hdd/power led and the whole nine yards.
Pressing any keys in any combination wouldn't wake the damn thing up, so I had to power cycle with the power button.
When it loaded up I got an error that xorg failed to start because "No screens" were found.  How the hell did that happen?!?  The "nvidia" driver was installed and working just fine prior to this... being crafty I had made a copy of xorg.conf which I promptly copied back into place but it didn't help and got the same error message.

I tried running the "sudo dpkg-reconfigure xserver-xorg" accepting the defaults and choosing "nv".  This time I got x to load, but the mouse wouldn't work and the background looks 16 bit.

HELP ME PLEASE!!!!

---

### Post by PartisanEntity on 2007-03-13
Hello,

Which version of Ubuntu are you using, and is this a laptop or a desktop?

---

### Post by jrekkedal on 2007-03-13
Latest Ubuntu Edgy on a desktop.... after looking at that post I did leave out quite a bit but it happens when you are damn frustrated I guess.

What boggles my mind is how I saved the backup of xorg.conf, but when i restored it the problem still happened?  Plus, my mouse won't work at all even though I tested it on another PC.

---

