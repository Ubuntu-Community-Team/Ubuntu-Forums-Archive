---
title: "Random Crashes like to piss me off......."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Hartxenon on 2008-01-23
Okay here's the situation, while just doing thing on my computer you know messing around on the internet listening to music, the normal things my computer likes to randomly decide to crash an open program usually it is the one I am currently using and usually that is firefox. This has been going on for a few weeks and one day i decided to run firefox in terminal to see what it tells me. Here is what i got....

> hartxenon@hartxenon-laptop:~$ firefox
The application 'gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Segmentation fault (core dumped)


does anyone have any suggestions to what i could do to remedy the problem that doesnt seem to go away??

---

### Post by jaytek13 on 2008-01-23
Well, the first question would be, are you running the latest version of Firefox? Segmentation Faults are essentially reserved to being the 'fault' of the program, as it occurs when a program tries to access a memory location that it shouldn't be accessing. 

Firefox has had many memory issues is the past so I wouldn't rule this out, which is why I ask. The latest FF version is 2.0.0.11.

---

### Post by Hartxenon on 2008-01-23
Yes i have the latest version of firefox I always update, but the thing is it isn't always firefox, firefox is just the program i have running the most, it has occured in amarok, and rosegarden and other programs.....

---

### Post by asmoore82 on 2008-01-23
have you ran Memtest86+ to test the RAM on this machine?
It should be in your boot menu.

---

### Post by Hartxenon on 2008-01-24
Wait, how would i do that, i mean when i used to dual boot i was given the option to choose, windows, ubuntu, or the memtest, but now i have an all linux machine that boots ubuntu automatically so im not given the option to choose that.

---

### Post by asmoore82 on 2008-01-27
> **Hartxenon said:**
> Wait, how would i do that, i mean when i used to dual boot i was given the option to choose, windows, ubuntu, or the memtest, but now i have an all linux machine that boots ubuntu automatically so im not given the option to choose that.

There should be a black screen with gray letters that says something about "GRUB;"
press Escape there to get the bootloader menu.

---

