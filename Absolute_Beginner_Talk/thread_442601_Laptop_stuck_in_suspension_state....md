---
title: "Laptop stuck in suspension state..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by jeisenst on 2007-05-13
I installed 7.04 for the first time on my AMD 64 laptop. The installation went fine, and everything seemed to be working, then I put the laptop into suspend. It won't turn back on.  The power light comes on, the screen remains black, the dvd drive spins once or twice and then the power shuts back off.  The whole process take about 15-20 seconds.  Any help would be greatly appreciated. 
Thanks

---

### Post by frrobert on 2007-05-13
Unplug it, pull the battery, wait for a minute, put the battery back in, plug it back in, and turn it on.  See if that works.

---

### Post by jeisenst on 2007-05-13
Still same problem...

---

### Post by KSI on 2007-05-13
I had the same problem when I first installed. Try adjusting your power management setting to reflect a non-suspending system. I haven't tried enabling hibernate, so I won't say whether or not that partiular setting will work.

---

### Post by jeisenst on 2007-05-13
Thanks, but first, I need to un-hibernate/un-suspend the laptop.  Anybody? I appreciate the help.

---

### Post by KSI on 2007-05-13
What kind of laptop are you using?

---

### Post by jeisenst on 2007-05-13
It's a ABS mayhem G-3. 3 years old, ATI radeon 9600/9700, AMD 64 processor, gig of ram, I was running xp before.  Would any other info help?  Thanks for the help!

---

### Post by KSI on 2007-05-13
I checked all my normal sources. Got nothing. ABS customer support says that they can probably walk you through it via phone: 1-800-685-3471 (8:30am-7:30pm PST Mon-Fri & 8:30am-5:30pm PST Sat)

Sorry I couldn't be of more assistance.

---

### Post by kenton_r on 2007-05-14
Try Booting up in recover mode in GRUB. Then once it is all the way up to a command line--enter "halt" which turns off the computer then restart normally.

---

### Post by pikul on 2007-05-14
Edit /etc/default/acpi-support and change:

SAVE_VBE_STATE=false #true is default

USE_DPMS=false #true is default


I did that and manage to fix my suspend mode, i haven't try to fix hibernate, make a copy of the file first :)

---

### Post by Michaelt74 on 2007-05-14
The hibernate and suspend options are very buggy with laptops. My suspend gives me the same problem - it shuts down and I can't access it without rebooting. When I hibernate, it works but after 'waking it', it freezes and starts doing weird things.

---

### Post by chewjoel on 2007-05-15
My problem is, the power never off when I turned my laptop off.  It seems everything has gone to rest, except for the screen: I still have ubuntu logo on my screen even though there's not a single sound indicating the laptop is working still, in anyway.

My laptop is Asus M2400N.

It was fine with Windows, power-off automatically after shut down.
But it doesn't work anymore after I changed to Ubuntu 7.04, so as my soundcard. :(

---

