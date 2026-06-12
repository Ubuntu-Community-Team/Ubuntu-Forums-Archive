---
title: "amarok freezeing"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by natman on 2007-07-26
I have amarok installed and used it a few hours back worked fine, i now try to open amarok and it pops up and all i get is the waiting symbol ( small watch in KDE ) and it stays like that for good. I have reinstalled it and it did nothing. Can someone please help??
I ran amarok in a terminal and found this perhaps it helps?
[HTML]natman@natman-laptop:~$ amarok
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
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
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
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x823e80 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x823e80 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?


[/HTML]

---

### Post by natman on 2007-07-26
Hi again,
I just poped in an xubunut cd and the sound works fine for, im kinda thinking i may have screwed up some sound files after using this 
> [http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+pavillion+sound](http://ubuntuforums.org/showthread.php?t=455147&highlight=hp+pavillion+sound)
Has anyone any ideas? should i just reinstall kubuntu?

---

### Post by forestpixie on 2007-07-26
I assume you are running kubuntu - I was reading this thread yesterday 

[http://ubuntuforums.org/showthread.php?t=509520](http://ubuntuforums.org/showthread.php?t=509520) (which is nothing to do with amarok before you look :) )

someone was worrying about removing ubuntu-desktop along with evolution, the answer was don't worry reinstall ubuntu-desktop if you need to 

Perhaps if you think you've deleted stuff you shouldn't have maybe you could install your desktop - or at least it would show if it was going to install files it needs !? 

 ie ```
sudo aptitude install kubuntu-desktop 
``` or ```
sudo apt-get install kubuntu-desktop
```  not sure whether it would be better to use one rather than the other in this instance, or to be honest if there is a difference

Just a thought - if it works it'd be quicker than a reinstall 

If nothing else I've bumped for you.

---

### Post by natman on 2007-07-26
Thanks for the info but i have a feeling that reinstalling the desktop will not do that much, im kinda worried that perhaps i may have altered the settings some where else deep down ( ie i may need a reinstall of linux itself).
Is there any sort of "system restore" for linux? or a way of getting my sound back!

---

### Post by forestpixie on 2007-07-26
not really sure - I don't think ther's anything in the way of a restore as such

Is it all of your audio and video apps which have lost sound.

I assume you've tried to purge and reinstall amarok, have you deleted the hidden amarok folder before you reinstalled?

---

