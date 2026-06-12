---
title: "Mouse missing in some apps"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by swedishlf on 2007-12-15
Hey folks,
  There are 4 different apps which are giving me problems with the mouse.  I suspect they are somehow related:
   DosBox, I get no mouse functionality
   Enigma (the game), no mouse
   Qemu - kvm - mouse appears to be stuck, right click responds but no motion.
   Neverputt - Slightest motion of the mouse causes wildly flailing screen

I've had this problem before in Feisty and running SDL_VIDEO_X11_DGAMOUSE=0 before I started kvm fixed the problem  this is no longer the case.

I'm now running Gutsy AMD64.

Anyone got any ideas for this rather odd mouse behaviour?

---

### Post by swedishlf on 2007-12-19
Well, I have solved it for qemu.  I actually run kvm and run it with sudo.  I did not run the export command with sudo.  Doing so solves the problem there.

Is there any way to run the export command at startup?  I've tried adding it to /etc/rc.local and also in the sessions -> startup programs menu with no luck.  Any ideas?

---

