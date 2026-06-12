---
title: "Screen Blacking out for no reason"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by The Burning Fool on 2008-02-01
I'm not exactly sure where this should go, but I am new to Ubuntu and linux.

I recently installed Ubuntu 7.10 on my laptop (Gateway CX2724 if that matters) and recently I've noticed that when I close the lid and open it again, the screen is completely black and the computer won't respond to any input.  I actually have to unplug the computer, pull the battery and restart the computer to get anything out of it.  I tseems to be happening only once or twice a day though, but still it is incredibly frustrating.

Any help would be much appreciated.  Thanks in advance.

---

### Post by ajgreeny on 2008-02-01
This will be the computer hardware setting to either hibernate or suspend the machine when you close the lid.  Waking from suspend is often a problem as far as I can see.  Try changing the settings to either do nothing, or shutdown the machine, when lid closed, and you might do better.  I don't have a laptop so can't remember where the settings are changed, but I'm sure you will be able to find it somewhere in the power settings system.

---

### Post by The Burning Fool on 2008-02-01
Nope, its not that.  I probably should have mentioned thats the first thing I checked.  Its not set to hibernate when the lid is closed, whether on AC power or battery power.

---

### Post by ajgreeny on 2008-02-02
Nor suspend?  It must therefore be set to do nothing when you close the lid - correct?

---

### Post by dstew on 2008-02-02
> Its not set to hibernate when the lid is closed,Where was this setting made (or not made)? In BIOS, in Ubuntu? Is the system dual boot? If so, does the WIndows system hibernate when the lid closes? Sometimes it is a BIOS setting. Some BIOSes will put the machine state into a small partition on the HD. I don't know if that is the case here, but is it possible that a suspend partition was removed or altered during Ubuntu install?

---

### Post by The Burning Fool on 2008-02-02
Okay, I think I got a hold of the problem.  I had it set to "blank screen" when I close my lid.  I changed that to "do nothing" and the problem seemed to stop.   Thanks for your help though.

---

