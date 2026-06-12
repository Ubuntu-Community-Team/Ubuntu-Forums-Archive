---
title: "How To: Ubuntu speed tweeks"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by evandec on 2006-06-04
So I have been using ubuntu for a couple weeks now and I really like it but I cant say its faster than windows. Is there a how to guide on speed tweaks for Ubuntu?

Best,
Evan

---

### Post by FryerFox on 2006-06-04
What is it specifically that you feel is slower? Boot time? Or possibly the office appliations or games?

---

### Post by evandec on 2006-06-04
Boot time is a little slower, not much though. Mostly just the time it takes to boot programs. 

It might take 10 seconds or so to boot up bashee or to load firefox takes signifigantly long than IE with windows.

---

### Post by FryerFox on 2006-06-04
Hmm. I can't say I've noticed firefox being slower than in Windows, but I do notice that KDE applications take a significant hit when loading in GNOME (maybe 3 seconds to load for Kate or KDevelop). This is because of a bunch of libraries they have to load that aren't normally loaded for GNOME apps.

As to boot time, is it possible that you are using most of your memory, so some swapping has to occur? You can find out if this is happening by adding a system monitor applet* to your taskbar and monitoring processor useage, memory useage, swapfile useage, and disk useage. 

This way, you can start a program and look at the graphs to find out if it's being limited by the processor, or having to swap memory to the hard drive, etc.

* In GNOME, right-click on the panel and click "Add to Panel". Scroll down to the Systems and Hardware section and select "System Monitor". Then when the little graph appears, right-click on it and select "Preferences". Check all the boxes you want to see (I just check all of them).

---

