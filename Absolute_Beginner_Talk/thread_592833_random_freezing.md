---
title: "random freezing"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2007-10-26
Hello, I was just wondering if there was like a error log or something i could see why my laptop keeps freezing at random, it never did this before, then yesterday it froze 3 times while surfing the web, and it froze a minute ago while the screen saver was running. Im not sure what could be causing it, so I was wondering if there was a way to check?

---

### Post by robinlennox on 2007-10-26
I have the very same issue... feels like I'm running XP when it first came out... i'm just missing the BSOD! :lolflag:

---

### Post by wpshooter on 2007-10-26
What version of Ubuntu are you using ?  Is it Gutsy ?

How long have you been running the version of Ubuntu that you are currently on ?

There is a syslog and I **believe** that it is located in /usr/log or something similar to that.  Just do a search on syslog.

There is a way to force it to do the system file check at bootup but I don't have committed to memory how you do it.  But I don't think I would attempt to do that until I have explored of avenue first.

---

### Post by twiceasworn on 2007-10-26
Most of the logs that are going to be of any use reside in /var/log

I would look at /var/log/messages, /var/log/syslog and /var/log/dmesg

---

### Post by DestroyMicroshaft on 2007-10-26
Im on gutsy, so which log would i get like a crash report out of?

---

