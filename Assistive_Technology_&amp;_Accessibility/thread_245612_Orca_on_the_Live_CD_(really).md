---
title: "Orca on the Live CD (really)"
date: 2006-08-28
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-08-28
Hi,

To all those who have been waiting patiently to try Orca: it has now finally made its way to the live CD (!).

The proof is in the CD manifest here:
[http://cdimage.ubuntu.com/daily-live/current/edgy-desktop-i386.manifest](http://cdimage.ubuntu.com/daily-live/current/edgy-desktop-i386.manifest)

We are still having some overflow issues so the AMD64 and PPC versions look over-sized and cannot be burned to CD, but i386 looks ok. Get it here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I'm just downloading it to test myself, but I'm assuming you have to start Orca from the command line. Don't rely on the Live CD boot option magic working at this point.

Try:

* Booting normally
* Alt-F2 followed by 'gnome-terminal' Enter
* Enter 'orca' and go through the setup
* Press Ctrl-Alt-Backspace to kill the gnome session
* Wait 30-40 seconds for it to log itself in again automatically
* Repeat the steps to start Orca

Please report any issues here, in Malone or on the mailing list.

- Henrik

---

