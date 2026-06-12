---
title: "Can I unmount my USB WinTV using software?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by dixonstalbert on 2007-09-22
Hello

I finally got my desktop to go into suspend to ram by replacing (Microsoft!) USB mouse and removing my USB external hub.

Works great- if I remember to first unplug my  USB WinTV. If its plugged in, my AthlonXP goes into Suspend, then wakes right up again.

I have tried rmmoding the modules I need loaded to run the WinTV:  Em28xx and usb_snd_audio, but suspend still doesnt work.

Is there some command or udev rules I could run in a script that would make my system believe the WinTV is no longer connected?

TIA

Dixon

---

### Post by ryanVickers on 2007-10-03
If you just unmount it before suspending, it should be fine, right?  A handy tool for this is the "Disk Mounter" applet for the gnome panel

---

