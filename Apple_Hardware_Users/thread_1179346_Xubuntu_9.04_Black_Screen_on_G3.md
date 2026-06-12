---
title: "Xubuntu 9.04 Black Screen on G3"
date: 2009-06-05
forum: Apple Hardware Users
---

### Post by colSolare on 2009-06-05
I installed Xubuntu 9.04(Alternate Install) for PPC on my iMac G3 333 w/ 288mb RAM. After the Xubuntu splash screen, the screen goes blank and goes into a suspend mode, but the computer is still running? By hitting Ctrl-Alt-F1, I can login and bring up a terminal. How can I change my video settings to start up the GUI? I'm pretty sure I have to revert my video settings to get the GUI to load. Help!!!

---

### Post by corsair67 on 2009-06-14
What I did was switched to console ctrl+alt+f1. Logged in with root and password. Changed to folder /etc/X11.  Using nano open xorg.conf to edit. (nano xorg.conf).
these are the changes I made to this file:

Section "Monitor"
    Identifier    "iMac"
    HorizSync    58-62
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
Monitor        "iMac"
    DefaultDepth 16
    SubSection "Display"
        Depth 16
        Modes    "1024x768" 
EndSubSection
EndSection
Restart system
It worked for me on my g3.

---

### Post by colSolare on 2009-06-16
I typed everything you entered and hit Ctrl-O to save and it said "Error writing xorg.conf: Permission Denied" .... now whats wrong?

---

### Post by cyberdork33 on 2009-06-16
> **colSolare said:**
> I typed everything you entered and hit Ctrl-O to save and it said "Error writing xorg.conf: Permission Denied" .... now whats wrong?
you have to have root-level permissions to modify xorg.conf. start your editor with sudo

---

### Post by maclinux on 2009-09-22
> **corsair67 said:**
> What I did was switched to console ctrl+alt+f1. Logged in with root and password. Changed to folder /etc/X11.  Using nano open xorg.conf to edit. (nano xorg.conf).
these are the changes I made to this file:

Section "Monitor"
    Identifier    "iMac"
    HorizSync    58-62
    VertRefresh    75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
Monitor        "iMac"
    DefaultDepth 16
    SubSection "Display"
        Depth 16
        Modes    "1024x768" 
EndSubSection
EndSection
Restart system
It worked for me on my g3.

I did all this, it started ok but then tells me it must run on low graphics mode.  What happened?

---

### Post by rjcalifornia on 2009-09-24
> **maclinux said:**
> I did all this, it started ok but then tells me it must run on low graphics mode.  What happened?

I know this one!! I know this one!! the depth and default depth should be "24" instead of "16"

---

