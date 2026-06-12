---
title: "problem with ubuntu and xp dual boot"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Torque313 on 2008-01-05
Here's the story:

I was doing fine with ubuntu and though i was still really new to it i loved it. I set it up on a different hard drive then my xp install and the two worked together flawlessly. Like usual everytime i booted up it went to the GRUB screen and i could choose which one to open. Everything was cool until something completely freaked out with xp and i decided to do a fresh install of it and assumed everything would be back to normal in a bit. That's when it all went wrong...

I reformatted the xp drive and re-installed windows on it and windows worked fine. After a while of messing witrh windows i wanted to go back to ubuntu and do some stuff so i restarted the computer. This time around it never went to the GRUB screen it just went straight into windows. when it booted up into windows i decided to look in here on the forums to see how i could get grub back. I found a thread (That i completely forgot the title of or i would post the link to it here) and it told me to throw in the ubuntu cd and write some stuff into the command line while linux was running off the cd to re-install GRUB. 
I followed the directions exactly and it worked perfectly exept for a major problem. When GRUB starts it looks just like it did when everything was working fine except i can't boot any of the two operating systems from it and get an error as follows:
ERROR 17: Cannot mount selected partition

and then it restarts grub again and says:
starting up...
Grub Loading Stage 2

and then returns to the grub menu

What should i do?
Take into account that i am a complete N00b to Ubuntu and linux in general and i will need this to be in terms that i can understand. All i want is for me to have my Ubuntu back and be able to start both that and windows from the GRUB menu. Pleeeeez help me :(

---

### Post by LouisChappell on 2008-01-05
If you have nothing that important on the HDD's I would recommend what i have done a few times;
use the XP boot disc to delete all partitions, then make a new partition for XP for x amount of gigs and leave the rest unpartitioned for ubuntu. Install xp, then use the guided install for largest amount of free space for ubuntu.
I have done this a few times due to balls ups (on windows behalf) and it sorted everything out real nice!

---

### Post by insertAlias on 2008-01-05
Reinstalling both OSs isn't a bad idea.  You might get away with just reinstalling Ubuntu (hope you made a /home partition).  Just remember for future reference, Windows installations overwrite grub with its own bootloader that can't boot anything other than windows.

---

### Post by eolson on 2008-01-05
Download a copy of supergrub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I'm a coward I always take the easy way out first.  If it don't work,  I give up.

---

### Post by Torque313 on 2008-01-05
i would love to except i have some really important stuff on the ubuntu drive that i can't get to through windows for some reason because it doesn't even see that drive. i have no idea why. I need to try to find a way to at least get it working long enough to pull my data off that drive and onto the safe one for data with no operating system on it.

---

### Post by eolson on 2008-01-05
That's what supergrub does.  It fixes your grub.  Normalizes it so to speak.

---

### Post by Torque313 on 2008-01-05
i can't use supergrub because windows isn't even seeing my cd drive. I have no idea why but it's number 8,234,568 reason why windows pisses me off. There has to be a way around this so i can at least get into ubuntu long enough to get mys stuff off that drive. I tried to use  a data recovery program on Hirens boot cd but it said it didn't recognise the file system on that drive. I have no idea why my computer is tripping out like this. does somebody have a way for me to get around this that doesn't involve burning another cd? all i want to do is start ubuntu.

---

