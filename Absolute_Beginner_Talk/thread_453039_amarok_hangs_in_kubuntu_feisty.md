---
title: "amarok hangs in kubuntu feisty"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by doctor bangali on 2007-05-23
Amarok is hanging in  Kubuntu, I simply can't get it to start. Any ideas?

---

### Post by Ek0nomik on 2007-05-23
What happens exactly?  Do you go to Sound & Video and click it and nothing opens?  Are you typing amarok in the Terminal and it just sits on that last command entry?

---

### Post by devicerandom on 2007-06-19
In my case, amarok just hangs when starting. No error messages at the terminal.

I guess the thing is related to the corresponding hanging of Firefox when it handles Flash content with sound.
Any hint?

---

### Post by adamklempner on 2007-06-19
If you start Firefox from terminal, does it happen to throw any errors when it hangs?

---

### Post by devicerandom on 2007-06-22
No. It just hangs.

---

### Post by Happy_Man on 2007-06-22
Yeah, stuff does that every now and then. What I always do is restart the session. Generally, it works then. Try that out.

---

### Post by devicerandom on 2007-06-22
Thanks, I'll try. It's quite a windows-ish solution, however. I posted details of the problem here: [http://ubuntuforums.org/showthread.php?t=481249]("http://ubuntuforums.org/showthread.php?t=481249")

Anyone can help me digging out this?

---

### Post by devicerandom on 2007-06-27
Restarting the session does not work. Any other hint?

---

### Post by devicerandom on 2007-06-27
Rebooting with arts disabled seems to work but let's wait...

---

### Post by rjfioravanti on 2007-07-24
i have same problem

it just hangs when i try to boot it up

If i boot from terminal I get th following output

 X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76e6c0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76e6c0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

---

