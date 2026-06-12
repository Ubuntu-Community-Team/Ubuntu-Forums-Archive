---
title: "Video in Beryl"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by sm1thson on 2007-01-17
Hi, Ive just installed Beryl (saw it on youtube -thats what made me finally make the switch to linux), its working well (some things like rain and snow dont work, but i dont feel like Im missing out with all the other good stuff in there!), but when i play the example video (experience ubuntu.ogg) in the default player (Totem movie player 2.16.2) it is blank! if i move the window the video shows, but then goes again if i rotate the desktop or anything. videos in youtube work fine in all conditions. my graphics card is the intel i915gm and i used [ this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft") (beryl, edgy, AIGLX) to install.

anybody know how to solve the video issue? (i am new to all this linux stuff)

---

### Post by sm1thson on 2007-01-17
found the answer and sorted it, here it is for referance:
```

'gstreamer-properties' from terminal.

Then go to the "Video" tab, changed the output to 'xwindow system (no xv)' on the drop down.

```
guess i should have searched harder before posting the first time!

---

