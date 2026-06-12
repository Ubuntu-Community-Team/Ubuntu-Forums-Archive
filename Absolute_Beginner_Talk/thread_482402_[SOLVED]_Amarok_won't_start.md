---
title: "[SOLVED] Amarok won't start"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-23
Hi - hope someone can help here.

Amarok got updated today to ver 1.4.6 - evreything was fine. But it has just stopped responding - couldn't close it, open it, start music at all. Had to reboot and it won't start at all now.

Tried running from the terminal to see if it gave me an error

```
kevin@kevin-desktop:~$ amarokapp

```

after 20 minutes this is the response - you can't see the flashing cursor though!

I've purged and reinstalled but still no joy.

If I can't get it to work - is it possible to revert to previous version?

---

### Post by raeb on 2007-06-23
> **forestpixie said:**
> Hi - hope someone can help here.

Amarok got updated today to ver 1.4.6 - evreything was fine. But it has just stopped responding - couldn't close it, open it, start music at all. Had to reboot and it won't start at all now.

Tried running from the terminal to see if it gave me an error

```
kevin@kevin-desktop:~$ amarokapp

```

after 20 minutes this is the response - you can't see the flashing cursor though!

I've purged and reinstalled but still no joy.

If I can't get it to work - is it possible to revert to previous version?

What happens when you try just amarok instead of amarokapp?

---

### Post by forestpixie on 2007-06-23
first time I did that it told me to do amarokapp - 

just tried again and i get the flashing cursor in terminal.

---

### Post by forestpixie on 2007-06-23
it's definetly trying to do something though - sys monitor shows it as running - with 3 amaroks!. But nothing is happening.

Just got used to it too :(

---

### Post by forestpixie on 2007-06-23
forgot attachment

---

### Post by Tynek on 2007-06-23
Hi ,I got the same problem after update to amarok1.4.6.When running in terminal I got this error messages
witek@witek-desktop:~$ amarok
```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098948 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098948 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
```
Any ideas how to fix it?
Thanx

---

### Post by forestpixie on 2007-06-24
bump

---

### Post by forestpixie on 2007-06-24
reinstalled ubuntu and all ok

---

