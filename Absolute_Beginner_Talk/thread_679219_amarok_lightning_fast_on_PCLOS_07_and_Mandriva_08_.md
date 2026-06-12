---
title: "amarok lightning fast on PCLOS 07 and Mandriva 08 but sloooow in Kubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2008-01-26
I am an Amarok fan and I have used amarok on various distros.

Kubuntu is my favorite but a major drawback is that regardless of whether I use Ubuntu or Kubuntu 7.10 and 7.04 Amarok is so slow.

It takes about 5 seconds to switch to next track in a playlist. It almost stalls the entire system when it updates the collection (3800 files in my case)

I use the option to have Amarok automatically monitor music folders for file changes, so my collection is always up to date. This is smooth and fast on PCLOS and Mandriva. But anything Ubuntu this is so slow. 

What is KUbuntu missing that these other distros have - it makes a big difference when using Amarok?

---

### Post by kellemes on 2008-01-26
Are you talking about the same versions of Amarok?
Also there may be a difference in compiled-in features, plugins etc..
When you run Amarok from the terminal do you get any informative output?

---

### Post by Harry789 on 2008-01-26
Yep - always same version

Here is brief output from terminal

alaan97ac@laan97ac-laptop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap                         p.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8272ba0 ): KAccel                          object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8272ba0 ): KAccel                          object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for Play                         listWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrL                         abelsChanged(const QString&)
laan97ac@laan97ac-laptop:~$

---

### Post by kellemes on 2008-01-27
Well, I just about have the same output when I run Amarok.. and it's not having issues at my end.
Do you get any terminal-output when you switch track? Or when it updates the tracklist?

---

### Post by Harry789 on 2008-01-27
that is just what I did, and the above is all I get. It is weird that PCLOS and Mandy are so much faster

---

