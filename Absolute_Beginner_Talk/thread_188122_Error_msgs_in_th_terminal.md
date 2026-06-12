---
title: "Error msgs in th terminal"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-06-03
Anyone knows what this error means? and how I can get rid of it? Kinda annoying, everytime I type something in the terminal with the sudo command this message comes.

sys:1: PangoWarning: Error loading GPOS table 4097

---

### Post by harishg on 2006-06-04
Got to do something which the pango program.Try to remove and install it again if it wont break any dependencies.

---

### Post by IsKall on 2006-06-05
reinstalled libpango-1.0 but it didn't work, What is Pango btw?

---

### Post by ChrisNiemy on 2006-08-28
Hi!

It's not a bug it's a feature.

No, ;) it's just a warning, or more than that it's a notification. 

It occurs together with Pango (uh, I think this has something todo with icons, metacity, and gtk) an specific fonts, mostly the "Dejavu" Fonts. Don't know exactly, still haven't fixed it on my system. But it is really not essential.

Just guessing, that maybe some fonts paths are not correct, maybe if one has commented out some lines in the /etc/X11/xorg.conf... don't know.

This behaviour was also listed as a bug. It should be fixed, but I don't see it ;)

Here's the link and the comments there are more interesting and useful than mine. :D

[https://bugs.freedesktop.org/show_bug.cgi?id=7455](https://bugs.freedesktop.org/show_bug.cgi?id=7455)

Greets -Chris

PS: Solution may be re-installing the package **ttf-dejavu** and **defoma** and some pango stuff. Or maybe downgrade ttf-dejavu. For me I have some additional non-ubuntu repositories and I think the "error" occured because I am using this version:
2.7-1bpo1 (don't know exactly where it's from)
but ubuntu dapper is default this version:
2.5-0ubuntu2
You can check this via package manager like Synaptic.

Perhaps still anybody else now has a proper solution to this error message?

---

