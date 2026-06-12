---
title: "USB ISSUE! Weird need help plz"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-18
Hi,

I'm running 32 bit breezy on a brand new install with an Asus A8N-CSM M-ATX and an Athlon processor motherboard. The USB works fine, but lets say I unplug my USB mouse, and then re-plug it back in....I get no Power to the mouse (or any other device). I have to reboot the machine in order the the USB mouse to power up or work. This can't be normal, can it? I have done several installs, mostly 64-bit  though, and this has never been an issue.

Is there anything that can be done as far as Ubuntu is concerned? I have checked the bios and everything seems to be in order. Any ideas out there?

---

### Post by 5-HT on 2006-04-18
What about a ```
 sudo /etc/init.d/hotplug restart 
``` after plugging the device back in?

---

