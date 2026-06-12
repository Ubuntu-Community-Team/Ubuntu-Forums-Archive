---
title: "Resolution screwed up?"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2007-12-04
I just restarted to install language packs and now my resolution is borked.

It claims to be 1024x768 )even though I set it to 1280x1024~ and yet it:s only displaying about 600x800. I:ve tried changing the resolutions but it just brings up the "is this resolution okay?" dialog without changing the resolution at all.

Oh but if I screencap the desktop is it the right size in the .png, but when I open the file in firefox I get about a third of the image.

---

### Post by philinux on 2007-12-04
you may have a backup of xorg.conf in /etc/X11 have a look in there first it might be called xorg.conf~

You'll need to use gksudo nautilus to reinstate a backup.

if that fails the in a terminal use

sudo dpkg-reconfigure xserver-xorg

The system will autodetect your hardware so mainly answer yes. Some screens are for info and require the user to press esc to continue.

---

