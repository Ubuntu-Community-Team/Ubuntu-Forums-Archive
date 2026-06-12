---
title: "JPEG2000 DVR Client Software &amp; Wine"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by frrobert on 2006-08-28
I have a security DVR that use a windows package for remote viewing called
Remote_J2K.exe.  I can not get it to work in Wine and there is no Linux version of the software.  Has anyone used this software with Wine or does anyone have any ideas of what software might work?


Thanks

---

### Post by dankegel on 2006-08-29
What version of Wine are you using, and what are the symptoms
of the problem?  I just installed with very current Wine
(post 0.9.20), and the app installed and started ok;
it misbehaved when I clicked on the 'setup' button, though.

---

### Post by frrobert on 2006-08-29
I'm using version 0.9.9-0ubuntu2 of wine. The first screen will come up but if I hit the connect or setup button it locks up.

---

### Post by nickmcg on 2007-02-15
I know this is a little late, but I just encountered the same problem.

Solution:

Moved the initial screen off to the side - the setup screen appears behind the main window & there appears to be no way to get the focus to the setup window if you can't see it.

Nick

---

