---
title: "KDE problem .."
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-11
Well everything was good last night, no problems. Now this morning i boot up only to find my resolution will only go to 1024x768. It was able to go up to 1600x1200 before just like in Windows, but not anymore. I'm pretty certain i didn't change anything. What could have made this happen?

Thanks

EDIT: Hmmm, i rebooted and everything seems fine. Weird, eh?

---

### Post by J.C. Denton on 2005-12-11
I had this happen on one Ubuntu machine before.  The resolution was set to 1280x1024, and on the next boot it had locked itself at 640x480.  For some reason, the xorg.conf was missing sync rates for the montior.  After adding the appropriate values, the problem went away.  I suspect that same problem is effecting your system as well.

On the system, at the GNOME desktop:
[LIST]
[*]Go to Applications->Accessories->Terminal
[*]At the terminal prompt type the following:
[/LIST]
```
grep -E 'HorizSync|VertRefresh' /etc/X11/xorg.conf
```
If you see two lines with those words, you're not experiencing the same problem I had, and we'll need to do some more troubleshooting.  If the command completes, and you're back at the prompt with no output, you'll probably need to add the sync values to your config.

If you're missing the sync values, reply, and I'll step you through the process.

---

