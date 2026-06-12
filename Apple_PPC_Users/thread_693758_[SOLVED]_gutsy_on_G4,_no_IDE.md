---
title: "[SOLVED] gutsy on G4, no IDE"
date: 2008-02-11
forum: Apple PPC Users
---

### Post by roadrocket13 on 2008-02-11
Bug#126337 has rendered my Mac an expensive doorstsop. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337)

unfortunately, i've tried all the solutions outlined in the Bug fix and have had no success on my G4 powermac (circa 2000, w/ DVD-rom and Zip drive)
if someone could recommend a course of action, that would be amazing. i'm a bit of a Linux noob (1 year with Ubuntu) and a total PPC novice.
i'm able to get to the Yaboot prompt after doing nothing or 4-6 cycles of;


```

First Stage Ubuntu Bootstrap
Press l for GNU/Linux,
Press c for cd-rom.

Stage 1 Boot: c
Booting CDROM ...

```


then;


```

Welcome to Yaboot version 1.3.13
Enter "Help" to get some basic usage information
boot: <tab>
     Linux old
boot: _

```


both "Linux" and "old" boot to a working Gnome GUI, except that there is no ethernet connection, no audio, and no CD-Rom recognition. though i can mount a USB pen-drive
i've tried holding C while booting, but that doesn't seem to work either. i also understand that PPC does not use a BIOS and i cannot seem to get to the OpenFirmware terminal. once i get to the GUI the system monitor tells me i'm using kernel 2.6.22-14 on Gutsy. the terminal seems to work properly so i can open, edit and save text files. however, modprobe ide-disk and modprobe ide-core seem to have no affect.

if i could just get a CD to boot, i'd downgrade to feisty and be fine with that.
thanks in advance.

---

### Post by stream303 on 2008-02-11
Have you tried burning a Feisty "alternate" iso?  Maybe at low speeds on good media?

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by stmiller on 2008-02-11
Yeah I second that. Try the Feisty alternative. Hold down the 'Alt' key when booting, and there you can pick the CD to boot from after a few seconds when the menu loads.

---

### Post by roadrocket13 on 2008-02-13
holding down the "Alt" button at boot time did the trick. thanks for helping out a PPC noob.

---

