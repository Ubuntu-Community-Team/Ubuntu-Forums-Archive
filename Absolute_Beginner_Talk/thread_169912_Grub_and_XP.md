---
title: "Grub and XP"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-05-03
I have little knowledge on Grub. I do know it allows me to control booting between my XP system and Ubuntu. I believe it right a second master boot record and simply hands off the booting to which ever OS you pick. Am I right so far? Last night  I was in XP to play a DVD and the usual program comes up and I click play. The video and keyboard go dead. That has never happened before. The system didn't crash. In fact I can access my files on the network. This problem couldn't have anything to do with having Ubuntu on another hard drive in the same box could it?

If I could get my Visioneer 7100 scanner to work in Ubuntu I wouldn't even use XP but no one has written a driver for it. Anyway, I just want to make sure that dual booting hasn't done something to XP.

Tim

---

### Post by jpkotta on 2006-05-03
There is only one MBR, and GRUB overwrites it.

Dual booting will not do anything to the XP partition.  If you really want to check, you can boot from the XP install CD, go to the "recovery console", and run ```
fixmbr
```
This will setup the MBR for Windows, as if GRUB was never there.  There are articles in the wiki to restore GRUB (there are many ways to do it, you will require a live or install CD).  I would strongly suggest only doing this if you are curious and don't mind fixing things.  It's completely unnecessary unless you want to remove Ubuntu.

It sounds like a Windows problem to me.  

Send a nice email to your scanner manufacture requesting Linux support.  It won't do anything, but if enough people do it, they will see that there is a demand and will release a driver.  It could be that there is a driver, but is not trivial to install and set up.

---

