---
title: "Ubuntu cannot be loaded"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by szymonnn on 2007-09-05
Hello, 
I was using earlier Ubuntu version 6.10 and everything was fine. I've made a fresh install of Ubuntu 7.04 including formatting partition and when I push power on my computer, my GRUB is loaded, then I choose Ubuntu to start, then Ubuntu is loading...loading and an error appears, something like that: HUB: connect-debounce failed, port 9 disabled. I cant use Ubuntu in normal mode, recovery mode and normal mode from cd. Only safe mode from CD works. What can I do to fix it out?

Cheers
~

---

### Post by bone2006 on 2007-09-05
Not exactly sure about the error, but possibly try removing everything connected to your USB ports and see if you can boot up then.  See if you can do an update as well once your able to boot in, if you are able at that point.

---

### Post by szymonnn on 2007-09-05
Yeah, I plugged off pen-drive and it loaded all right. Thank you.

---

### Post by Crafty Kisses on 2007-09-05
> **szymonnn said:**
> Hello, 
I was using earlier Ubuntu version 6.10 and everything was fine. I've made a fresh install of Ubuntu 7.04 including formatting partition and when I push power on my computer, my GRUB is loaded, then I choose Ubuntu to start, then Ubuntu is loading...loading and an error appears, something like that: HUB: connect-debounce failed, port 9 disabled. I cant use Ubuntu in normal mode, recovery mode and normal mode from cd. Only safe mode from CD works. What can I do to fix it out?

Cheers
~

You should try booting in verbose mode, to see where it actually fails, you can do this by pressing ```
Alt+F2
```

---

### Post by szymonnn on 2007-09-06
Well, a small problem still exists, ubuntu can be loaded, gnome starts, everything's cool, but when I want to use console and press ctrl+alt+F1, then the same problem appears, a black screen is displayed and it crashes with log-in thing. I mean that I press ctrl+alt+F1 and I see all time something like:

HUB: connect-debounce failed, port 9 disabled.
HUB: connect-debounce failed, port 9 disabled.
HUB: connect-debounce failed, port 9 disabled.
HUB: connect-debounce failed, port 9 disabled.
HUB: connect-debounce failed, port 9 disabled.
HUB: connect-debounce failed, port 9 disabled.

...

And I can't do nothing and I'm forced to restart computer manually. I have nothing plugged in USB ports, same everything about USB is turned on in BIOS. Such problems started to happen to me when I upgraded Ubuntu from version 6.06 to 6.10 and with version 7.04 I have also same problem.

---

### Post by alienexplorers on 2007-09-06
Just a stupid question, but why don't you use the internal terminal instead of Console Terminal.

---

### Post by bone2006 on 2007-09-06
Have you been doing an upgrade via the update manager?  You should consider download the latest 7.04 CD, formating the HD without the USB device connected, then before doing anything do an update, reboot and see if your still having problems.  Just a suggestion

---

