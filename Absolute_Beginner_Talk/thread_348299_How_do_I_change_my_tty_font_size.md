---
title: "How do I change my tty font size?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-01-28
My Gnome and KDE GUI interfaces look good (I managed to get the correct driver for my video card installed!).

But if I logout of the GUI to use the TTY / console (_not_ to be confused with a Terminal window running within a GUI), the text:

[LIST]
[*]Is too large

[*]Begins and ends outside of the top and bottom edges of my display device
[/LIST]

Is there a reasonably straightforward way to change this?  I don't want to screw up my GUI -- it's working right -- but it would be very helpful to know how to configure TTY mode so I can read everything...

(Also, is there a simple way to exit TTY / console mode and return to the GUI-based login?  Both the "exit" and "logout" commands leave me stuck in a TTY login/password loop, and "reboot" isn't what I want to do...)

Cheers & thanks,
Ric
SFO

---

### Post by steve.horsley on 2007-01-28
I believe that you add a clause at the end of the grub line, like **vga=xxx** where xxx is a number. This gives some numbers you could try:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

### Post by Phrawm48 on 2007-01-29
Okay -- so far, so good.

In */boot/grub/menu.lst*, appending the *vga=nnn* parameter to a particular boot option does indeed change the tty resolution. So for example,

> kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda7 ro quiet splash

becomes

> kernel		/vmlinuz-2.6.15-27-386 root=/dev/hda7 ro quiet splash vga=793

(By the way, the VESA numbering from the link Steve provided is invaluable when specifying *nnn* ...)

BUT the now-smaller text still begins two characters too far to the left: A text line that should read *abcde *appears on the screen as *cde*.  (Vertical alignment of TTY is now corrected, albeit  to the top and bottom-most pixels on the display...)

Note that the left-alignment behavior is not a result of changing the text size, but rather a behavior that existed previously.  Indeed, I thought changing the text size would also remedy the left-alignment problem as it has the vertical alignment issue.  Alas, no.

Any ideas how I can fix the alignment problem?  Or should the issue become a new, separate thread?

Cheers & thanks for the help,
Ric
SFO

---

