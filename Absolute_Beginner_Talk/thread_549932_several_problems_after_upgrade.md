---
title: "several problems after upgrade"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-09-13
Hey guys, I just upgraded from 6.06, to 6.10 and then to 7.04 in the same day and I'm getting several annoying problems, first of all, gedit won't open from a terminal, so I can't edit a lot of stuff I need to. Then I got a lot of errors trying to install anything with add/remove and synaptic (codecs, etc), then I installed Amarok and I can't make it work, I get the config screen, and when it tries to load it won't, on firefox even after installing the needed plugins for java and macromedia, any website with movies (such as youtube) crashes Firefox and I have to kill it. Besides all that, any gksudo or dialog lets me choose options, it just freezes and again, I have to kill it. 

Hope someone knows what could possibly be happening, if I have to post any logs or outputs let me know and I'll post them if I don't get any more errors. I've been trying to make this things work for 10 hours straight and I think I'll just lose my patience if I see yet another error or messed up window, hehehe. 

Thanks in advance. 


Oh, here's what I get when I try to open amarok:
```
desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098218 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098218 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
Amarok: [Loader] amarokapp probably crashed!

```


I would post the output of "sudo gedit /x/x/x" but all I get is frozen text editor, same thing happens with anything with "dpkg" on it.

---

### Post by codesplice on 2007-09-13
Maybe try doing a clean install of Feisty rather than doing two updates?  There are a lot of changes that occurred between 6.06 and 7.04, and I wouldn't be at all surprised if that upgrade resulted in some broken packages.

In the meantime, you can always use nano and apt from the terminal rather than gedit and dpkg :-)

Also, try running
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
 to make sure you have the latest versions of your installed packages. 

Good luck!

---

