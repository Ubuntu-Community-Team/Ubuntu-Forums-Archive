---
title: "Urgent Please Help"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-08
I just installed Doom 3.  I thought everything was good to go... then I start the game and halfway through the intro-movie it crashes out to the desktop.  My sound was working perfectly before.  After the crash... nothing... no sound.  I have two physical sound cards... Esonique PCI (Alsa) and Intel ICH5 (Alsa)  The intel is on board sound card.  I checked in the volume control to make sure I still had the PCI card checked, which I do.  Now the second issue is with the message board.  The reason I am not using spaces between paragraphs is because when I hit enter - just with the forum while writing posts) Firefox crashes to desktop.  So, I installed Doom 3.  It crashes during the intro movie, I have no sound now, and I cant hit enter on this forum without Firefox crashing....  I don't know what to do now...  any help would be much appreciated.

---

### Post by tyggna1 on 2007-09-08
I'd try reconfiguring your GUI.
The terminal command for that is:

```
dpkg-reconfigure xserver-xorg
```

This *should* set your Graphical User Interface (xserver) back to the way it was when you first installed.

---

