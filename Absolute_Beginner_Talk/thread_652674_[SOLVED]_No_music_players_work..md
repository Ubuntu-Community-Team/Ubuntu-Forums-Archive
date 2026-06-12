---
title: "[SOLVED] No music players work."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by fullmetalgerbil on 2007-12-29
Tonight Amarok quit running-everytime I tried to play a song a message came up saying the device was busy. I uninstalled and reinstalled it, same thing. Then I went down the line and tried every other media player on the add/remove list. None of them worked. They installed, but just wouldn't play. I'm about to take the blunt insturment approach and format the hard disk then reinstall Ubuntu fresh as I haven't an iota of a clue as to why this is happening or how I can fix it. Any help would be vastly appreciated.

---

### Post by mikewhatever on 2007-12-29
You may get a clue of what's going on in the background by starting Amarok from the terminal. Simply type the name and look out for errors, post here if any.

---

### Post by tgalati4 on 2007-12-29
You may have a firefox plug-in (like Flash) that has jammed the music channel.

In a terminal:

>sudo killall firefox-bin

It's a common problem.

---

### Post by fullmetalgerbil on 2007-12-29
Thank you for responding. I ran Amarok in terminal and this is what I got:
> Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap


---

### Post by fullmetalgerbil on 2007-12-29
So if I do the >sudo killall firefox-bin command I lose flash? and if I dont I dont get no music?

---

### Post by fullmetalgerbil on 2007-12-29
Took things into my own hands. You were right tgalati4 it was a firefox plugin-the Fasterfox addon. I uninstalled it and things are once again peachy with the tuneage:guitar:. Thanks for pointing me in the right direction.

---

### Post by meindian523 on 2007-12-29
Please mark the thread as solved

---

### Post by tgalati4 on 2007-12-29
I'm running Flash 9 with Linux Mint 4 (based on Gutsy) and when listing to cocgospel.com the player locks up at times and kills all other audio.  By killing firefox-bin sound is restored.  Bringing up firefox again allows flash again, but I know there is at least one major memory leak with flash and probably other problems that will cause trouble.

---

