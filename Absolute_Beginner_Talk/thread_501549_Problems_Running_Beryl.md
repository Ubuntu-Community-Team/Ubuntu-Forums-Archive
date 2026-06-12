---
title: "Problems Running Beryl"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Matt Nichols on 2007-07-15
I am attempting to run Beryl on Ubuntu 7.04 with a nVidia graphics card (which is enabled). I have installed and reinstalled the packages from synaptic, though I still get this same problem:
```
matt@matt-ubuntu:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

Any ideas how I can fix this problem to run Beryl? Oh yeah, and after all that, I loose my window frames, and toolbars. Thanks for the help.

---

### Post by Happy_Man on 2007-07-15
Press alt-f2 and enter the command ```
beryl-manager
```

Then, run ```
emerald --replace
```

If you didn't install the package emerald-themes, do that first.

---

### Post by Matt Nichols on 2007-07-15
Okay, cool, I got the red emerald in the tray. It didn't seem to do anything to my theme though, so I changed the window manager (I think) from the Ubuntu default to beryl, which did nothing. I then tried compiz with the same thing, and my window frames dissapeared and it froze. I had to Ctrl+Alt+Backspace to get out. The same thing happens every time I try to run beryl-manager now. I tried reinstalling, but to no effect. Any suggestions? Thanks.

---

