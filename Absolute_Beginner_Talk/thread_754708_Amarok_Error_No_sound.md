---
title: "Amarok Error/ No sound"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by grewolf on 2008-04-14
[COLOR=Black]I am using Gustsy Gibbon 7.10 and Gnome 2.20.1 and I had sound before but now no matter what application I use I have no sound.  As per one of the posts ran application in terminal and got this error 

  [/COLOR]```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81bb358 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81bb358 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
```

---

### Post by joshrobinson on 2008-04-14
i posted a fix for amarok and pulse audio (the new audio from hardy heron)
im not sure if it will work in this situation, but its worth a shot if you want to try it

[http://ubuntuforums.org/showpost.php?p=4648593&postcount=2]("http://ubuntuforums.org/showpost.php?p=4648593&postcount=2")

---

