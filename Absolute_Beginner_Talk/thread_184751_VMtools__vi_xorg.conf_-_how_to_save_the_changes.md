---
title: "VMtools / vi xorg.conf - how to save the changes?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by itsmeagain on 2006-05-30
Hi I have just installed VMtools into my Ubuntu 5.10 that is running as a guest on VMware.  Part of the instructions that I am using tells me to open a Terminal window and type **cd /etc/X11 **and then **vi xorg.conf**.  This opens the xorg.conf window, I make my changes to the file but I do not know how to save the changes. The instructions tell me to press the "**ESC**" key > type "**w**" and then type "**q"**, but nothing happens. If I close the window and then reopen it, it is just as before. Can any body advise how to save the changes?

I got around the problem by doing this "**sudo gedit /etc/X11/xorg.conf**".  I then made the changes and saved them. This did what I was trying to do with (vi). By the way what I was doing was making changes so that the mouse cursor stays within the VMware window until CRTL+ALT is pressed.

Thanks

---

### Post by Klaidas on 2006-05-30
If you want to save a file in vi, as I remember, it's ```
ESC
:
wq
``` And then hit the ENTER key :)

---

### Post by richbarna on 2006-05-30
Esc
:wq
If you get a permission problm, just put ! after the command.

---

