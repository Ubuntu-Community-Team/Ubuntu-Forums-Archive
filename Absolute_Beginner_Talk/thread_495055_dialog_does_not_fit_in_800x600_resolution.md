---
title: "dialog does not fit in 800x600 resolution"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by kellygreer1 on 2007-07-07
Not sure if this is considered a bug.  I wonder what the Gnome folks consider the lowest resolution they are targeting?  But I noticed a Gnome dialog that doesn't fit in 800x600.
note: I am using Fiesty Fawn

The 'Login Window Preferences' dialog seems to be to long to fit on a 800x600 screen and therefor also would not fit on a 640x480 screen.

Anyone else consider this a bug?

Thanks,
Kelly [kellygreer1]

---

### Post by e_james on 2007-07-07
I know exactly what you mean. I was using a low resolution to suit a TV as monitor and it was really awkward to work with administration dialogs. Maybe not a bug. If the fonts adjusted with resolution it would probably work better but this would likely take a lot of effort.

---

### Post by anewguy on 2007-07-08
I'm just a beginner myself, but I can tell you what seems to be the fix in my case.  I had this same problem when using the default "vesa" driver in /etc/X11/xorg.conf.  When I installed the correct driver for my video IGP and changed xorg.conf to reflect it, those problems went away.  It seems to be a very common problem, and one I hope someone addresses in an upcoming release or update.  It wouldn't be so bad, but I cannot get the window to resize small enough to get to the selection boxes.  Perhaps some of these apps need to check the running resolution and adjust themselves accordingly.

---

