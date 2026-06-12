---
title: "anyone here use zsnes??"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-12-25
I always used to play znses with my roms on Ubuntu 7.04, but now I've upgraded to Gutsy.  I installed the program and when I start it from the menu it opens for 2 seconds then it closes.  I went through formatting my computer, because of other problems, I reinstalled the program and still had the same problem.

Heres what it says when I run it through the terminal: 

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/malek/.kde/socket-maleks-laptop.
can't create mcop directory


I see stuff about permisions so I try sudo znses and now:
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Creating link /root/.kde/socket-maleks-laptop.
can't create mcop directory


so can anyone who's experienced with this emulator or know how to solve the problem speak up. THX






and also if you know about other Super Nintendo Emulators that WORK, I'd like to know.

---

### Post by sc30317 on 2007-12-25
I see some permissions problem.  Who knows, try sudo zsnes in the terminal?

I have zsnes in gutsy, and its working flawlessly

---

### Post by frup on 2007-12-25
Snes 9x is around somewhere but most people seem to prefer zsnes I think.

---

### Post by gigaferz on 2007-12-26
[http://ubuntuforums.org/showthread.php?p=3694819](http://ubuntuforums.org/showthread.php?p=3694819)

I am about to do it.

So I am assuming that this happened after installing Kxmame??

Because it was working fine before...
I also edited my xorg.conf and im using a different driver, but thats no reason for snes to ask for a kde folder...

It did help me to fix zsnes

---

### Post by Xorg.conF on 2007-12-26
yea thanx for the link giga, I did the second method where you change alsa09 to alsa, and it works fine.

---

