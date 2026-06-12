---
title: "Laptop won't start: processes killed by BUS signal?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by ian.m.montgomery on 2007-11-05
Complete n00b here with a startup problem; I checked the previous threads on this but don't see anything that I recognize as a similar problem. I have been running Ubuntu 7.04 fine for about a month or so. I've installed all updates so far, but haven't upgraded to 7.10. 

I've been running Ubuntu okay since day 1 with my hardware, except for the occasional disk check snag (after 34 boots it kicks in automatically), but even then I can insert the live CD, go to terminal and run the check to repair. Otherwise, no problems thus far.

So, I try to boot up today and get the following errors:

[INDENT]init: rcS main process (2386) killed by BUS signal[/INDENT]
[INDENT]rc-default main process (2387) killed by BUS signal[/INDENT]


I'd like not to re-install if that can be avoided, and I don't quite know what this error means (bad hardware? Should I even bother with re-installing??). Any help you good, knowledgable folks can give is much appreciated!

Cheers,
Ian

---

### Post by SpiritIsReality on 2007-11-06
howdy
looks like you've come across something new.
[http://www.google.ca/search?hl=en&q=%22main+process+%28*%29+killed+by+BUS+signal%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22main+process+%28*%29+killed+by+BUS+signal%22&btnG=Search&meta=)
being unknowledgeable, that's the best I can do at present.
will be interesting to find out what it is. from a knowledgeable somebody.
will dig around for Bus stuff.
trails.

[http://www.google.ca/search?hl=en&q=%28ubuntu+%7C+debian%29+%22BUS+signal%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%28ubuntu+%7C+debian%29+%22BUS+signal%22&btnG=Search&meta=)

---

### Post by K.Mandla on 2007-11-06
Hi Ian. What happens after those error messages appear? Does the machine lock up? Does it continue to boot? Are you left at a text screen?

Also, what kind of computer are you using? Can you give us some specifics?

---

### Post by ian.m.montgomery on 2007-11-06
[INDENT]What happens after those error messages appear?[/INDENT]

Nothing, really--they appear on the black background, after the BIOS screen but before Ubuntu loads. It seems "locked up" at that point, since nothing happens, but I can type and have it appear on that screen. I don't have the terminal prompt in that screen, though (i.e., "ubuntu@username:").

I'm running 86x Ubuntu on a Gateway laptop with an AMD 64 core 2 duo processor. (I have the 64-bit ubuntu disk, but some skimming of forum posts suggested it was probably safer to install the 86x instead.) That's about all I remember about the machine, but if there's other relevant info, let me know what that is and I can try to find out.

---

### Post by ian.m.montgomery on 2007-11-06
Update on my computer's specs:

Gateway MT6452 
AMD Turion 64 X2 Dual-Core 
160GB HDD

Hope this helps. Please let me know if there's some other info I can post that might be helpful to know.

---

### Post by charlatan1978 on 2007-11-06
QUOTE]I've been running Ubuntu okay since day 1 with my hardware, except for the occasional disk check snag (after 34 boots it kicks in automatically), but even then I can insert the live CD, go to terminal and run the check to repair.[[/QUOTE]

If you are having to carry out repairs on your hard disk there may be a fault with it.  Do you know the make of the hdd?  If so I would download the diags from the manufacturers website and check your hard disk.

---

### Post by ian.m.montgomery on 2007-11-06
Maybe there is a problem with the HDD, but my reason for running fsck was because of the automatic HD checks that come up after so many mounts (around 30 or so). A similar problem is described here:

[http://ubuntuforums.org/showthread.php?t=150136](http://ubuntuforums.org/showthread.php?t=150136)

[http://ubuntuforums.org/showthread.php?t=367644](http://ubuntuforums.org/showthread.php?t=367644)

I basically got similar error status on boot b/c the fsck tried to run automatically after 30 or so mounts, so I put in the live CD to run GNOME editor, try the partition, then put the commands into the terminal (all described in the second link above).

---

