---
title: "kTorrent randomly closes..."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-07
I never really notice it, seems to happen when I am not looking. Starts back up fine...but it really is annoying. Anything i can check? btw, it usually runs for at least 5/10min...

---

### Post by pbw on 2007-06-07
I had this issue as well, though not quite as frequently as yourself. I just built it from svn and the problem was solved.

---

### Post by RomeReactor on 2007-06-08
Hi. You can try running it from the terminal (if you're on Ubuntu) or Konsole (Kubuntu):
```
ktorrent
```
Then, when it crashes, look at the messages it leaves there and post them here. It may be useful to diagnose the problem.

---

### Post by FleetAdmiral74 on 2007-06-08
uh oh, this already looks ugly when I run it...

```
ed@ed-desktop:~$ ktorrent
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
ed@ed-desktop:~$ 

```

it does run fine though...

---

### Post by RomeReactor on 2007-06-08
FleetAdmiral74, is this the output of the crash? Also, are you running Ubuntu (Gnome) or Kubuntu (KDE)? If your desktop is Gnome, it may be a [known bug]("https://bugs.launchpad.net/ubuntu/feisty/+source/ktorrent/+bug/109184/comments/25"); it looks like a problem with QT libraries, but I know almost nothing of that, so I can't be of help. Sorry.

---

