---
title: "Imac G4 external screen"
date: 2005-09-12
forum: Apple PPC Users
---

### Post by nicolas314 on 2005-09-12
I have a 2002 IMac G4, the one that looks like a lamp. I use it together
with an external monitor plugged onto the VGA-out, because the main
built-in screen has been damaged. This works fine on OS X.

I recently installed Ubuntu on the machine and could not get the external
monitor to mirror the built-in screen. VGA-text mode is correctly replicated,
but anything graphical is screwed. What I see on the external monitor seems
to be completely out of sync. Obviously the signal is getting through and
from what I can get it seems set to the correct frequencies. What can I do?

This is more desperate than it seems. The main built-in monitor is too damaged
to think about using it for anything. My only view into this computer is through the
external screen. Googling has not turned anything useful.

The video card is reported as Nvidia GeForce 2 MX 400, correctly identified
and handled by X.org. 

Thanks for helping

---

### Post by nicolas314 on 2005-09-13
Answering my own question... I leave a trace here of what I did, hoping it might
be useful to someone else.

I finally got the external monitor going! The trick was simply to modify
xorg.conf to add a few options to the "nv" module. Basically, an Imac G4 comes
with a GeForce 2 MX, which is completely supported by x.org (at least for 2D
stuff). This board comes with two outputs, which are re-directed in the iMac:
one for the internal LCD screen (1024x768 max), one for the external output.
The required options for "nv" are:

Option "CrtcNumber" "0"
Option "FlatPanel" "off"

Not sure about what the second option does exactly since I do not have the
LCD screen any more. The first one forces output on the external plug, which
is what I needed.

As a result, I am now running Ubuntu on an iMac G4 connected to an external
monitor at 1600x1200 resolution. Quite impressive, especially since Mac OS
(Tiger) installed on the very same machine does not allow more than 1024x768
on the external monitor. Obviously this is something locked in software on the
Mac OS side.

---

### Post by fat on 2006-09-20
can you post your xorg.conf file.  I have a working monitor and want to try dual displays if this is possible

also - are you having problems with your virtual terminals.  Ctrl-Alt-F1 to F6 gives me a garbled screen.

Thanks

---

### Post by anuragj71 on 2006-10-18
Hi,
I was in the same situation with busted LCD and external CRT pegged at 1024x768 - on macosx 
This tip works great ! Now I have 1600x1200 display .
Thanks a lot for sharing this information -

---

