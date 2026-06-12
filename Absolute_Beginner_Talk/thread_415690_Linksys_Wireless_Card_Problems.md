---
title: "Linksys Wireless Card Problems"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by BrooklynDodgy on 2007-04-20
Howdy everyone!

I'm very excited to join the Ubuntu (and Linux in general!) community, and installed Feisty Fawn last night, and am looking forward to plunge right in (and finally leave M$FT behind)!

I had some difficulty in booting up Ubuntu, having the loading screen freeze  when trying to boot in "regular mode" with both the Caps Lock and Scroll Lock lights were blinking.  When I tried loading it in "Recovery Mode" I would end up getting a "Kernel Panic" error message and it would stop.  I realized somehow that I when I removed my wireless card (Linksys WPC11v3) before booting the computer, Ubuntu would load just fine.  Once I logged on and pushed my card back in, my computer would freeze up, unable to respond even when I took my card out, with the Caps Lock and Scroll Lock lights blinking.

Any ideas on how I can get my Wireless up and running on Ubuntu without freezing up my computer?  (Keep in mind that given this issue, I don't have Internet access when on Ubuntu, only when I'm using my Windows XP partition).

Thanks!

Cheers,
BrooklynDodgy

---

### Post by Immolatus on 2007-04-24
What model is the wireless card?
Your going to have to search for the Linux firmware for this card and save the file to external media (cd ,memorystick,thumb drive ect.) and then install the extrcted files into /lib/firmware and then shut down, plug in the card startup. 
The hard part will be locating the firmware. We are both using feisty so we have the exact same generic drivers in /lib/firmware and I don't see anything about anything made by Linksys.

This link might help you.
[http://www.extremetech.com/article2/0,1697,2111770,00.asp](http://www.extremetech.com/article2/0,1697,2111770,00.asp)

or more likely this one
[http://www.linuxquestions.org/questions/showthread.php?t=462105](http://www.linuxquestions.org/questions/showthread.php?t=462105)
good luck.

---

