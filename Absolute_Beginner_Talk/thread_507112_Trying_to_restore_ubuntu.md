---
title: "Trying to restore ubuntu"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-07-22
I foolishly tried to update my nvidia drivers and now I can't get into ubuntu.  Of course, I'm a complete noob.  When starting up, there's lots of stuff happening on the screen but when completed I get a blue dos type screen with "failed to start the X server (your graphical interface). It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  Yes ---No. "
Yes brings me to a screen with an error message at the bottom stating " API Mismatch: the Nvidia kernel module has the version 1.0-7184 this X module as the version 1.0-9755. Please make sure the kernel module an all nvidia driver components have the same version.:

What can I do to get it back to where it was....sorta like a safe mode to uninstall what I obviously did wrong?
Thanks

---

### Post by w4ett on 2007-07-22
From the command line type:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the graphical interface to reset your xorg. the most basic video driver selection is : vesa  this SHOULD get you back into a GUI

---

### Post by pcostanza on 2007-07-22
Wow, thanks for the quick and extremely helpful reply.  I'm back in and won't soon try messing around again.
Appreciate your help.

---

### Post by w4ett on 2007-07-22
No Problem...Good Luck

---

