---
title: "How come I always receive error message when starting KDE app from Konsole??"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-23
Currently using Kubuntu Feisty Fawn Edition.

Everytime I start an application from command line via Konsole Interface I always receive the following:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


The application always starts without problems however.  Is there a way to supress or just correct whatever is causing this error message??

---

### Post by Happy_Man on 2007-05-24
That has no issues whatsoever. I get the same error code, too. Never had a problem with it.

---

### Post by Terl on 2007-05-24
I get it too.  I haven't figured it out either.  The app runs fine.

---

### Post by Sparkster185 on 2007-05-24
Same thing happens to me (like others said), and I don't know why or how to fix it.  I just CTRL-C and go on my way.

---

### Post by aidanr on 2007-05-24
afaik it's because of the wacom devices in your xorg.conf, you can remove them or comment them out if you don't have a wacom tablet, just backup your xorg.conf first

---

### Post by kevdog on 2007-05-24
I found this link, maybe this will solve the problem!

[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

---

