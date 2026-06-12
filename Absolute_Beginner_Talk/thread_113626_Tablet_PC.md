---
title: "Tablet PC ?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Robert Marley on 2006-01-06
Howdy Y'all!

I was wondering if Ubuntu can function correctly on a Tablet PC (using the touchscreen)?

Would I need any additional software to do this?  If so, what would you recommend?

Thanks in Advance,
Robert Marley

---

### Post by gruepig on 2006-01-08
You don't need any software beyond what is in ubuntu.  You may need to install some wacom packages.  (A quick search of available packages suggests xserver-xorg-input-wacom and maybe wacom-tools; you can install these using synaptic.)

You'll need to determine what tty the touchscreen uses.  I'm not sure exactly how you would do this; if you are currently running Windows, you can probably use the device manager or some such to tell you.

You'll need to edit /etc/X11/xorg.conf, adding some InputDevice sections.  See this post: [http://ubuntuforums.org/showthread.php?t=63186](http://ubuntuforums.org/showthread.php?t=63186).

Good luck.

---

