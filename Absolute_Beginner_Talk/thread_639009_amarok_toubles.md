---
title: "amarok toubles"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by missed her show on 2007-12-12
hallo

I've tried to remove Amarok and reinstall, with no luck.   What's happening is, it will start up, and then just "disappear: (crash?). 

I've removed and reinstalled with no help. 

I need a solution to fix this or another app that can handle my 80+gb collection + 2nd gen iPod etc.  Any suggestions?

---

### Post by nae5 on 2007-12-12
Was there an icon in upper right that you might have missed? if not, youre going to want to run amarok in the terminal and paste the output for the experts around here. If a program crashes you should try running it with the terminal which will give error messages about why it couldn't start if none appeared launching with the GUI.

     Amarok is considered the best music app among many Ubuntuans, it is also good for ipods if it works with yours.  gtkpod is an option for ipod, and rhythmbox for playing music files, Though Amarok imo is worth the troubleshoot.

---

### Post by missed her show on 2007-12-12
hey thanks!

here's what happened.   I reinstalled via Terminal, and first run it didn't crash, and actually played thru two songs before this:

```
dewey@dewey-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80980a0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80980a0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
dewey@dewey-desktop:~$ QImage::smoothScale: Image is a null image
*********************************WARN_ONCE*********************************
File r300_mem.c function r300_mem_alloc line 225
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c0009a

```

and then this after running it again, crashes immediately. 

```
dewey@dewey-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x836c438 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x836c438 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
dewey@dewey-desktop:~$ *********************************WARN_ONCE*********************************
File r300_mem.c function r300_mem_alloc line 225
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c0009a
dewey@dewey-desktop:~$ 

```

any ideas?

---

