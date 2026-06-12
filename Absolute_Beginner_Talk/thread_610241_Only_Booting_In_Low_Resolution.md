---
title: "Only Booting In Low Resolution"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-11-11
New user to Gutsy.  The system was working fine with proper resolutions and Compiz working nicely.  

Okay, I tried to follow some complex (at least to me) instructions regarding using a 5 button mouse.  Some new files were created, etc.  When I went to reboot to Ubuntu, I could only reboot in low resolution mode (800x600) and could not change the visual effects from "NONE".  I worked my way backwards undoing all the changes (since they didn't work anyway) and now I still can't boot in normal mode or change visual effects.

I hope I haven't somehow totally screwed up and have to reinstall.  Any help is much appreciated.

---

### Post by Nano Geek on 2007-11-11
Try this:```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by sagesparrow on 2007-11-11
that did it.  thanks.

if you have a moment and it's relatively simple, could you explain why that would have happened?

---

### Post by Nano Geek on 2007-11-11
> **sagesparrow said:**
> that did it.  thanks.

if you have a moment and it's relatively simple, could you explain why that would have happened?Well, I'm not sure what instructions you followed, but I'm guessing it asked you to edit you x.conf file which handles all of your input devices: keyboard, mouse, display, ect. And maybe the instructions told you to do something that erased that file which caused Ubuntu to switch to 800x600 resolution.

---

