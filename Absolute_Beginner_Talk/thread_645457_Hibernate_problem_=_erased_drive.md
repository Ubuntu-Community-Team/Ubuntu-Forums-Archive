---
title: "Hibernate problem = erased drive?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by idrumlots on 2007-12-20
Allright, I'm not really new to computers or anything, and I have had Gutsy now since its release... I really was handling everything well till I decided to test out this hibernate mode (my computer has many lights on it)... 

First off, I'll describe my system:
nvidia 7950 (which I got working beautifully eventually)
the rest is awesome. AMD64 5000x2 etc...

I am dual booting, I have a drive for windows and then another drive partitioned in half with windows and linux, so to boot to linux i just hit F8 when my system starts up and select slave drive.

So I test out this hibernate feature and my computer refused to wake, respond, or otherwise change whatsoever from its hibernation. I thusly manually turned it off. Upon reboot, I hit the ol' F8 only to find Slave drive was no longer an option. Reluctantly, I went to windows... where the partitioned drive with the windows stuff still existed. I rebooted to ensure a clean shutdown, hit f8, to no avail, no slave drive operating system. I then re-entered windows, checked the partition manager and HOLY MOLY it says the linux partition is 100% Free....

Why? Please, please is this reverseable? I just... Linux was being so good to me

Any help is appreciated, thank you

---

### Post by hyper_ch on 2007-12-20
now that shouldn't not happen... are you sure the linux partition is free? Download Supergrub LiveCD and check it out with that.

---

### Post by idrumlots on 2007-12-20
I will try that, I suppose it is possible that it is just still in some sort of suspend? Maybe it's just not being read correctly; either way I'll have to try this soon, thank you! 
I'll report back with results-

---

