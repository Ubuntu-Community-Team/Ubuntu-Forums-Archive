---
title: "trying to get beryl to run"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
joonsuk@Joonsuk:~$ beryl-manager --no-force-window-manager
joonsuk@Joonsuk:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
beryl-manager --no-force-window-manager

wat do i need to do seems like im missing the Xfree86DRI and other things

---

### Post by kittyhawk63 on 2007-07-06
If you're using an ATI video card and Feisty Fawn 7.04, go to the site shown below and follow the instructions. There are three pages. Please, make sure you copy and paste the lines to avoid any errors. If you have a mouse with a wheel: highlight the line and go into "terminal" and click down on the mouse. It will automatically paste the line for you. That will keep you from having to right click <copy> and then right click <paste>.

[http://www.howtoforge.com/ubuntu-feisty-beryl-ati-radeon](http://www.howtoforge.com/ubuntu-feisty-beryl-ati-radeon)

It's a great piece of script and it works.
Hope you can use it.
kh

---

### Post by matthew101 on 2007-07-10
i am having a similar problem with running Beryl

unfortunately i cannot access the above website, it says "You are not authorized to access this page."

any ideas?

thanks

---

### Post by matthew101 on 2007-07-10
ah dont worry, got it working manually :s dunno why it didnt work

---

### Post by JParkus on 2007-07-10
It might not be any help but when I first started using Beryl I wasnt using the restricted drivers and without those I has no Beryl.

---

