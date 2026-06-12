---
title: "Cant get direct rendering"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-25
Hello! i need some help with getting 3D acceleration to work. i have a ATI Radeon X850 XT graphics card.
i have just installed fglrx. and when i write fglrxinfo in the terminal i get this

armcandy@armcandy-desktop:~$  fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT Platinum Edition Generic
OpenGL version string: 2.0.6011 (8.28.8

i also wrote glxinfo and it gave me this

armcandy@armcandy-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

wich just shows that i do not have direct rendering. How can  enable it.??

---

### Post by wpshooter on 2007-02-25
Did you edit your /etc/X11/xorg.conf file by putting in fglrx instead of ATI - see below:

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

Then reboot.  Make sure you save an OLD copy of the file before you make changes.

---

### Post by hempa on 2007-02-25
> **wpshooter said:**
> Did you edit your /etc/X11/xorg.conf file by putting in fglrx instead of ATI - see below:

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

Then reboot.  Make sure you save an OLD copy of the file before you make changes.
no i did not edit the file. how can i edit it with kwrite?? i am using kde.
what command should i write in the terminal if i want to edit the file.
thanks for the help

---

