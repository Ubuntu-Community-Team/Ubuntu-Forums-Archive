---
title: "kTorrent closes after a few hours..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-09
Even w/ the initial errors, it seems to work fine for some time. Right at ed@ed-desktop:~$ Qt: Warning: QObject::disconnect: Unexpected null parameter, is when it closes though. Well, I have not been here for when it actually crashes, but it is always stable when those QT Warnings are up.

```
ed@ed-desktop:~$ ktorrent
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
kbuildsycoca running...
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
Qt: Warning: QObject::disconnect: Unexpected null parameter
ed@ed-desktop:~$ Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QGArray::at: Absolute index 0 out of range
KCrash: Application 'ktorrent' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

```

---

### Post by orb9220 on 2007-06-09
Did you install kTorrent from synaptic? or the .deb from here [http://ktorrent.org/](http://ktorrent.org/) as this is newer and fixed alot of bugs that are in the one in the repo's.

---

### Post by starcraft.man on 2007-06-09
Feisty Backports has the latest build (just checked synaptic). So if you enable those you should be able to get an easy update :).

---

### Post by FleetAdmiral74 on 2007-06-09
I just installed the ktorrent from synaptic, not sure if I used a fiesty backport...

---

### Post by starcraft.man on 2007-06-09
> **FleetAdmiral74 said:**
> I just installed the ktorrent from synaptic, not sure if I used a fiesty backport...

Easy way to check you have right version is to open up any terminal and type this in:

```
ktorrent -version
```

will output the version of Ktorrent at the bottom. Should be  2.1.4.

---

### Post by FleetAdmiral74 on 2007-06-10
Qt: 3.3.7
KDE: 3.5.6
KTorrent: 2.1

I seem to be missing a .4, is that important?

---

### Post by scunc_dvl on 2007-08-28
Mine crashes the exact same way and is 2.1 without the .4, so that must be. I'll definitely be updating then enjoying hte smooth ride later, hopefully :)

---

