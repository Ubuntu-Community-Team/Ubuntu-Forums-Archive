---
title: "Wine in Ubuntu ??? &gt;-&lt;"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by catle on 2007-02-14
When I try to run any window softwares by using Wine, I always get the message on the command line :

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

What happened with me? How can I fix it?
Many thanks for your help.
:popcorn:

---

### Post by Sklasko on 2007-02-14
I'm not an expert when it comes to working with WINE but when you installed WINE, did you launch winecfg to set everything up. Perhaps that might be the problem? I'll look around and see if anyone else has a similar problem.

---

### Post by justin whitaker on 2007-02-14
> **catle said:**
> When I try to run any window softwares by using Wine, I always get the message on the command line :

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

What happened with me? How can I fix it?
Many thanks for your help.
:popcorn:

Are you running the correct drivers for your system? WINE is looking for part of the Xlib library that does not seem to be installed. 

Also, did you try running it as root? Maybe it is trying to establish a call that requires that sort of access.

What are you trying to run? Did you "wine notepad" to see if WINE is installed correctly?

---

