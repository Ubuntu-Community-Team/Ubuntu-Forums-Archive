---
title: "gtk libraries in Gnome?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-02-16
If I install the gtk libraries in Ubuntu Edgy, will it allow me to run basic KDE-targeted apps in Gnome? 
Is it safe to do so or is there the potential to create Gnome / KDE conflicts?

---

### Post by dbbolton on 2007-02-16
which kde apps do you want to use ?

---

### Post by Stunt Double on 2007-02-16
Kmagnifier.

---

### Post by Stunt Double on 2007-02-16
I installed KMagnifier (kmag) without installing the gtk libraries to see what happened.
 
It works perfectly but I'm not certain how to read the terminal output:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...

Does it mean that it can't run in "X" but that Gnome includes "kbuildsycoca" which can run it?

I had also tried xzoom as a magnifier but Kmagnifier is far superior.

---

### Post by dbbolton on 2007-02-17
i'd say that if the app works, don't worry about it.

i get strange error messages when i launch nautilus or gedit as gksudo, but they function soundly.

---

### Post by jordanmthomas on 2007-02-17
kde apps do not require gtk libraries.  You do need qt libraries, which will automatically be installed.  If you're using ubuntu you already have gtk stuff installed.

GTK = Gnome
QT = KDE

the errors you posted are common and don't really pose any sort of problem.  I assume kmag works fine for you, correct?  It would still put those errors out if you ran straight KDE to start with.  I can't seem to find exactly what they are, but I have read up on them before and they are benign.

((edit)) if I remember correctly, they had to do with wacom devices being in xorg.conf.  If you don't have wacom devices (touchscreen maybe?) these errors are presented.  I think the solution was to just get rid of all the wacom stuff in xorg.conf

((edit2)) Yep, I removed the references to wacom in xorg.conf and I don't get the errors.  -- Arch Linux, but shouldn't be any different

---

### Post by Stunt Double on 2007-02-17
Thanks for the help. 
Kmagnifier does work well except for a few quirks. Rotation doesn't work. Also, whenever I increase the magnification from X2 to X3 and then back to X2, the active part of the magnification window is reduced. I have to go to X1 and then back to X2 to correct it.

---

