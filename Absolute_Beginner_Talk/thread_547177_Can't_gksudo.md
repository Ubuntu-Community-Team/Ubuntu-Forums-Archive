---
title: "Can't gksudo"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by dsbw on 2007-09-09
Doing a gksudo or a "sudo nautilus" or anything that would open a GUI from the command line I get:

 "Gtk-WARNING **: cannot open display:"

This happens on a 7.04 fresh install regular and server (with desktop installed). Both are running NVIDIA cards.

---

### Post by andrewPCT on 2007-09-09
Are you doing this from a Terminal window (Applications -> Accessories -> Terminal?

---

### Post by dsbw on 2007-09-09
> **andrewPCT said:**
> Are you doing this from a Terminal window (Applications -> Accessories -> Terminal?

I had no idea that was necessary so....no.  

That works. I get this now when I do "gksudo gedit":

(gedit:11716): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

"gksudo nautilus" seems to work fine with no errors.

---

### Post by dsbw on 2007-09-09
And just to add, since this is the newb section: I was trying to do it from Ctrl+Alt+F1(F2, etc) terminals.

Thanks.

---

### Post by Maestro23 on 2007-09-09
> **dsbw said:**
> And just to add, since this is the newb section: I was trying to do it from Ctrl+Alt+F1(F2, etc) terminals.

Thanks.

Do you have "gedit" installed?

---

### Post by dsbw on 2007-09-11
Yes, I believe so. Why?

---

### Post by mcduck on 2007-09-11
> **dsbw said:**
> And just to add, since this is the newb section: I was trying to do it from Ctrl+Alt+F1(F2, etc) terminals.

Thanks.
You can't run graphical applications if you are not inside a running X session. Gedit and Nautilus and other GUI programs can't work from command line. That explains the error about not finding a display.

The authentication error is a known bug, but as it doesn't cause any actual problems (other than the error message) it's not very high-priority bug. Just ignore it and you'll be fine.

---

### Post by rsambuca on 2007-09-11
> **dsbw said:**
> I had no idea that was necessary so....no.  

That works. I get this now when I do "gksudo gedit":

(gedit:11716): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

"gksudo nautilus" seems to work fine with no errors.

That is a known bug with gksudo and gedit, but it still works.  For now, just ignore it.

---

