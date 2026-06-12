---
title: "VLC play my m4a files but Amarok not, any solution?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-25
Hi
Thank you for reading my post
I have some mp3 file which their type is m4a.
when i open them using amarok it return an error about codecs 
but VLC can play them.

Is there any way to make Amarok play them too?

I installed all codecs that are mentioned in stiky thread.


Thanks

---

### Post by legolas_w on 2007-05-26
Hi
Any comment is far more than welcome.


thanks

---

### Post by jiminycricket on 2007-05-26
Hi legolas, can you copy the exact error that Amarok gives you when you try to play an m4a file?  Or even run it in a terminal, and see what error message comes up.

---

### Post by legolas_w on 2007-05-26
Hi
Thank you for reply.
I execute the amarok command in a terminal
here is terminal output:

```

legolas@legolasPC:~$ amarok
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
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097340 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097340 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow


```

and here is the exact error message that amarok showd

```

Error Loading Media
There is no available decoder.
file:///media/sdb5/music/The marine (2006) OST/09 the road .m4a

```



Thanks

---

