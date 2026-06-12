---
title: "Gutsy installation freezes"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by insideblasts on 2007-11-07
Hi. I'm trying to install 7.10, dual boot with XP. The live CD (tried 3 or 4) loads fine, but then freezes on desktop (mouse sporadically stuck, then no movement at all). I've tried a few times and have managed to start the install but after more than 30 minutes of freezing have had to give up. The process has got as far as language, or location, or not even that. My machine has 256MB RAM (not great I know, but should be enough). CD is rotating and making active noises. Any help? I know a bit, but am not yet confident with command line. Thanks

---

### Post by oilchangeguy on 2007-11-07
> **insideblasts said:**
> Hi. I'm trying to install 7.10, dual boot with XP. The live CD (tried 3 or 4) loads fine, but then freezes on desktop (mouse sporadically stuck, then no movement at all). I've tried a few times and have managed to start the install but after more than 30 minutes of freezing have had to give up. The process has got as far as language, or location, or not even that. My machine has 256MB RAM (not great I know, but should be enough). CD is rotating and making active noises. Any help? I know a bit, but am not yet confident with command line. Thanks

i'm suprised you got to the desktop. the problem is the amount of ram your computer has. if the video is onboard, it's taking some of that 256. the best thing you can do is upgrade the ram. with all of the anti-virus, and anti-spyware crap you need to run with windows, your windows system must take a long time to load the desktop. 256 is not enough for today's computers. if you can't upgrade the ram, then i suggest xubuntu.

---

### Post by droppedd on 2007-11-07
Try the alternate (text mode) install CD. It still walks you through the process, only with a much uglier interface :) but no real command-line knowledge or anything is necessary, so no need to worry about that.

---

### Post by P4man on 2007-11-07
One piece of advice: if you are having trouble in the live CD environment, do not install!
I have no idea what is causing it though; could it be something with the cd? try checking it for errors (its an option in the cd boot menu). Also, if your mouse freezes, does the keyboard still work ? Try pressing control+alt+F1, and see if it drops you into a console (ctrl+alt+F7 will return you to the gui)

Are you having any sort of trouble at all in XP ?

---

### Post by oilchangeguy on 2007-11-07
> **droppedd said:**
> Try the alternate (text mode) install CD. It still walks you through the process, only with a much uglier interface :) but no real command-line knowledge or anything is necessary, so no need to worry about that.

the os may get installed. but with the low amount of ram available. it will probably run slow.

---

### Post by insideblasts on 2007-11-07
Thanks. At the moment (recently re-installed XP) have minimal requirements on RAM, no anti-virus... Also, if booting from live CD, surely XP isn't using RAM at all? I might be wrong! I'll try Xubuntu or alternative CD.

---

### Post by P4man on 2007-11-07
> **oilchangeguy said:**
> i'm suprised you got to the desktop. the problem is the amount of ram your computer has. .

No its not. I have run Ubuntu on a machine with 128Mb RAM. Its not exactly pleasant, but it works. The official minimum requirement is 64Mb!

---

### Post by oilchangeguy on 2007-11-07
> **P4man said:**
> No its not. I have run Ubuntu on a machine with 128Mb RAM. Its not exactly pleasant, but it works. The official minimum requirement is 64Mb!

uh, it is when it comes to using the live cd. pay attention, before you post.

---

### Post by insideblasts on 2007-11-07
Thanks all. P4man: No problems with XP (apart from the usual). I'll try the keyboard.

---

### Post by P4man on 2007-11-07
> **oilchangeguy said:**
> uh, it is when it comes to using the live cd. pay attention, before you post.

Hmmm, well, ok. The site mentions 256Mb minimum for live cd (Gutsy)
[http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)

(I did run live cd for Feisty on a 128Mb machine, and it worked.)

One way or another, I wouldnt expect Gutsy to just freeze if it runs out of memory. At worst, the kernel might panic, but not a system freeze.

All that said, I do agree Xubuntu is probably a better choice for a  256Mb machine.

edit: never mind, in ubuntu kernel panics do cause freezes. Had them myself. Only indication was blinking keyboard LEDs, so who knows, maybe it is the problem..

---

