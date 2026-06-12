---
title: "Using Magic Trackpad"
date: 2010-10-14
forum: Apple Hardware Users
---

### Post by gino90 on 2010-10-14
Hello world!:P

I recently upgraded to maverick and wanted to ask: how can i make my magic trackpad work with it?
Pairing,single-finger pointing and tap to click work great out of the box,but two finger scroll,two-finger tap etc don't work at all!(the option "two-finger scrolling" in the touchpad tab isn't enabled)

---

### Post by kosumi68 on 2010-10-16
> **gino90 said:**
> Hello world!:P

I recently upgraded to maverick and wanted to ask: how can i make my magic trackpad work with it?
Pairing,single-finger pointing and tap to click work great out of the box,but two finger scroll,two-finger tap etc don't work at all!(the option "two-finger scrolling" in the touchpad tab isn't enabled)

If you want to build and install yourself, you could try this project: [http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

You could also switch from the evdev X driver (default install in maverick) to the synaptics X driver, by adding this to your /etc/X11/xorg.conf:

```

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "synaptics"
#    Driver "multitouch"
#    Driver "evdev"
EndSection

```

The utouch project ([https://launchpad.net/utouch/](https://launchpad.net/utouch/)) aims to provide more complete gesture support, but currently lacks some functionality provided by the above alternatives.

---

### Post by gino90 on 2010-10-16
Hi!
Thank you for your answer,first of all!:)
Could you tell me what differences there are between the three projects you mentioned?
I had a look on all of them,and synaptics driver should be the most stable but has the least features,if I don't go wrog,utouch has most features of all but is still in development,while the new xf86-input is somewhere in between.
Is it right?:)

---

