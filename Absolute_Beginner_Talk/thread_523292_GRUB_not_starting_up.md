---
title: "GRUB not starting up"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-11
GRUB and Ubuntu is installed on my external hard drive.  Windows XP is installed on my internal hard drive.  Whenever I chose to restart my computer from Windows, the BIOS loads all the RAM, and then just sits there. I end up having to manualy turn it off, and then turn it on again.  When I turn it on again, it works fine (The BIOS loads the RAM, and then goes into GRUB).  When I restart from Ubuntu, it works fine.  Why doesn't it work when I restart from Windows?

Thanks.

---

### Post by shearn89 on 2007-08-12
probs cos its an external drive, it needs to do something to "turn it on" and then connect? Not sure how to solve though - i'll do some googling...

---

### Post by sailor2001 on 2007-08-12
for windows that's sitting on it's own harddrive:  fixmbr   grub is mounted on your other hardrive

---

### Post by Yes on 2007-08-12
shearn, I figured that that was the problem (The external hard drive shut downs shen not in use, and so it shuts down when I use Windows.  When I restart the computer, it fails to start up, and because GRUB is on the external hard drive, it fails to start.)  I've looked into it, and couldn't find anything, but if you do find ssomething, please let me know.

Sailor, what do you mean by "grub is mounted on my other hard drive"?

---

