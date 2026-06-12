---
title: "Does Nvidia: &quot;Separate X Screens on One GPU&quot; work reliably?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by doriard on 2007-04-25
I have dual monitors and I want each one to be independent, so that wallpaper, games, etc. don't show up in the center, spanning half of each monitor.   I have both monitors working now, but I want to improve it.  I'm guessing that the 

nvidia-xconfig  --separate-x-screens

command will do that.  Is this true?  What file(s) do I back up in case it doesn't work -- just xorg.conf?

---

### Post by doriard on 2007-04-25
I found most of my answer on the Nvidia website:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-p.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-p.html)

Partially pasted here:

While there are several disadvantages to this approach as compared to TwinView (e.g.: windows cannot be dragged between X screens, hardware accelerated OpenGL cannot span the two X screens), it does offer several advantages over TwinView:

    *

      If each display device is a separate X screen, then properties that may vary between X screens may vary between displays (e.g.: depth, root window size, etc).
    *

      Hardware that can only be used on one display at a time (e.g.: video overlays, hardware accelerated RGB overlays), and which consequently cannot be used at all when in TwinView, can be exposed on the first X screen when each display is a separate X screen.
    *

      TwinView is a fairly new feature. X has historically used one screen per display device.

So, I guess I want to stick with TwinView for now, until the two X-screen, Nvidia/X server combination allows moving windows between X screens.

---

