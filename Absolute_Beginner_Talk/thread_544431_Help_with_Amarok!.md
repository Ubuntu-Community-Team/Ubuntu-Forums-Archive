---
title: "Help with Amarok!"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-09-06
I installed Amarok, and seem to like it a lot, but I have a problem I would love help with.

1. My music is located on my other hard drive, and when I try to drag the entire folder (50 gb+), Amarok crashes. I then tried to add just 1 album , thinking that the program can't handle that much information at a time, and then it said something along the lines of "Amarok can't play mp3's" and gave me a link to update it, but everytime that comes up it has already crashed so I can't click on it to update the codecs or whatnot.

I've searched around the program for a link to update the codecs so I can play mp3's, but can't find anything, does anyone have a link to their codecs or something I can type in the terminal?

Thanks!

P.S. I googled it and found a site that told me to put this in terminal for that same problem:

```
sudo apt-get install libxine-extracodecs
```

Didn't work for me!  :(

---

### Post by dptxp on 2007-09-06
Lot of users find problems running Amarok

Here is a thread where I got solutions, I had removed Amarok by then. Did not try again.
[http://ubuntuforums.org/showthread.php?t=445828](http://ubuntuforums.org/showthread.php?t=445828)

This is about getting mp3 support for Amarok.

---

### Post by trippinnik on 2007-09-06
the last time i got that error i deleted the .xine folder in my home directory and it worked. i don't know about the other thread as i never had to do all that.

---

### Post by Wiebelhaus on 2007-09-07
Amarok is THE reason I started to and still do use linux , anything you have to endure to make it work is well worth it imo.

but anyway
> 
sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

---

### Post by alwiap on 2007-09-14
Amarok still has no sound, although I can hear sound elsewhere :(

I typed 'amarok' in console and this came up.

```
alex@alex-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8130be8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8130be8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

```

suggestions?

---

