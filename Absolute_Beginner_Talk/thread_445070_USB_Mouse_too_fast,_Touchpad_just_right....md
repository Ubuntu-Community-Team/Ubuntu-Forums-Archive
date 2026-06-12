---
title: "USB Mouse too fast, Touchpad just right..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2007-05-15
Hi all,

Is there anyway to specify the speed/acceleration of my USB mouse?  The settings in Gnome only seem to affect my touchpad.  Is there any way to set them separately?

Cheers,

Sully

---

### Post by mahy on 2007-05-15
I found out a nice workaround:

open the xorg.conf file 

```
sudo gedit /etc/X11/xorg.conf
```

Now find the stanzas about your mouse and the touchpad. Touchpad will probably be listed as the "CorePointer", while the mouse will have the "SendCoreEvents" in its stanza. All you have to is to SWAP those lines. Then save the file, restart the X server and from that moment on, the gnome mouse settings will affect your usb mouse only (not the touchpad).

---

