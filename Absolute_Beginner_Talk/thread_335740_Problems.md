---
title: "Problems"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2007-01-10
Hi all,

I restarted my computer today (only thing I changed was installing some updates).  I couldn't boot into ubuntu, it failed when beryl tried to load.  Ok, I removed the auto start entries from command line, no problem.

Now, when I try to start Kaffeine to play a DVD, X restarts.  If I open Kaffeine on its own, It says Cannot talk to klauncher.  If I click "Xine Settings", X restarts.

See below.
Any ideas greatly appreciated.
Matt


matthew@matthew-desktop:~$ kaffeine 
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
/dev/dvb/adapter0/frontend0 : : No such file or directory
QLayout "unnamed" added to QWidget "unnamed", which already has a layout
kaffeine: ERROR: : couldn't create slave : Cannot talk to klauncher
kaffeine: ERROR: : couldn't create slave : Cannot talk to klauncher
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
matthew@matthew-desktop:~$

---

### Post by Hurricane on 2007-01-11
Just bumping this, it's bugging me quite a bit.  Even launching beryl-manager causes X to restart.

---

### Post by Hurricane on 2007-01-11
Reinstallation of my nvidia drivers fixed this problem.

---

