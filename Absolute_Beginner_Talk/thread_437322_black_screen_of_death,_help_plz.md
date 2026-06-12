---
title: "black screen of death, help plz?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by trackerbishop198x on 2007-05-08
so much for linux stability over windows.  i installed the ati drivers that came with ubuntu for my ati x1950pro card and now i get the black screen on bootup after seeing the ubuntu load screen. how can i recover from this without starting all over again?  thx a lot.

rant: 

im using an early 2006/2005 card so i wouldve thought that by the april 2007 update we'd have support for all ati cards seeing as how half the userbase has them and ubuntu is trying to replace windows.  

also why does ubuntu punish me for using an amd64??  I wanted to install flash player but I had to do it through the terminal in a 10 step roundabout way (found it on this forum) whereas non amd64 users get to install flash player easily.

---

### Post by calraith on 2007-05-08
Can't really blame the Linux community for spotty support for Flash and Radeon, as Adobe and ATI respectively do not publish open specs for their software.  Try finding Flash for Windows XP or Vista 64-bit editions, and you'll see it's not just a Linux thing.

But I digress.  If the ATI driver you have installed isn't working, hit Ctrl-Alt-F1 to get to a console, modify xorg.conf to load driver "vesa" instead of "ati," and reboot.  From there, you can either scour ATI's website for an appropriate driver, or try using [envy]("https://launchpad.net/envy") to install the appropriate ATI driver.  For what it's worth, I once had a laptop with an integrated Radeon Mobility of some sort for which no Linux ATI driver seemed to work.  Performing an lspci -v indicated some completely different manufacturer, like the video chipset was merely based on a Radeon reference design, and not an actual Radeon card.

---

### Post by Iceni on 2007-05-08
There was no flash in windows xp x64 for the longest time as well. I don't know if it is there now, but it was not when I was running it.

---

### Post by H.E. Pennypacker on 2007-05-08
> Can't really blame the Linux community for spotty support for Flash and Radeon, as Adobe and ATI respectively do not publish open specs for their software. Try finding Flash for Windows XP or Vista 64-bit editions, and you'll see it's not just a Linux thing.

That's funny.  I've never thought of that.  It's something I could add to my arsenal.

---

### Post by trackerbishop198x on 2007-05-08
i see, i didnt know that either.  thanks:P

---

