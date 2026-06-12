---
title: "Widescreen notebook..."
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by grahamroese on 2006-06-10
Hey guys!

I was playing at a rock concert the other night. The other band at the club was promoting Ubuntu. I had already tried out some other distros of Linux before (mostly Red Hat and Fedora stuff, y'know), so I was more than enthusiastic about getting a copy home. DOn't get me wrong, though, I'm certainly no Linux whiz! However, before I go ahead and install Ubuntu, I have one question:

If at all possible, how can I configure Ubuntu to function properly with the wide screen on my Compaq Presario V2000 notebook?
I run it with an ATI RADEON XPRESS 200M video card, if that makes any sort of difference.

Thanks *so* much for your help!

---

### Post by grsing on 2006-06-10
Yeah, I've got it running on a widescreen on a desktop, and it works fine.  Probably, it'll be autodetected when you set it up and work out of the box (though there might be difficulties with the ATI card, they're not so great on the drivers, but I'm far from an expert on that, and I know there are ways to make it work).

---

### Post by Belathor on 2006-06-10
and if it doesn't detect the widescreen you can run
> sudo dpkg-reconfigure xserver-xorg in the terminal and you can manually set the resolutions that you system can use.

---

### Post by grsing on 2006-06-10
Yep.  And if for some reason you get a strange condition where the desktop is bigger than the screen and so scrolls when you go to the edges (happened to me at first), just make sure the resolution is set to the right one in the System Preferences.

---

### Post by grahamroese on 2006-06-10
Thanks guys, I think I'm ready for an install!

---

### Post by Skye on 2006-06-10
grahamroese, I have a Compaq v2000 series (v2402us) laptop, and I can tell you for a fact that the ATi x200m-based widescreen is detected and works fine out of the box.  I'd be happy to answer any questions or help with any problems you might have, just PM me.

EDIT: For typos.

---

