---
title: "Evolution hangs on startup for about 7 minutes"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-12-27
I'm using Evolution with the Exchange server at work. It takes about 7 minutes to start up and 
here's what it says in the terminal while I'm waiting...
```
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CalDAV Eplugin starting up ...
```
Then after about 7 minutes, it shows this and evolution pops up
```
/bin/sh: /usr/bin/esd: not found
```

Any idea why it's taking so long to start up? I've purged evolution and reinstalled many times. 
Thanks in advance for your help!

---

### Post by shanepardue on 2006-12-28
I just reinstalled the operating system to get the same problem even with a fresh install of kubuntu.

---

### Post by da_bears on 2007-02-02
Hi. Same problem here, and tried same approach of complete reinstallation of ubuntu. No joy. My system hangs for about 10 min on installing CalDav Eplugin, then evolution is a bit sluggish afterward.

I've not come across a solution here or in other forums...if you do pls do post and I'll do likewise.

This problem has kept me from fully switching to ubuntu because my firm uses an exchange calendar. But eventually I'm sure I'll find a solution and will be able to shrink the windows partition to nada.

---

### Post by shanepardue on 2007-02-02
Unfortunately, I never found a solution. The problem does seem to stem from the plugin though. I since have abandoned evolution altogether as I was not happy with it's performance. My work wants me on windows while I'm there anyway to retain windows knowledge for support, bleh.

---

