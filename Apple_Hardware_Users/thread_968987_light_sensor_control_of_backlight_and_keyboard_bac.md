---
title: "light sensor control of backlight and keyboard backlight"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-11-03
How do I set the screen and keyboard backlight to be controlled by ambient light like in OS X?

---

### Post by cyberdork33 on 2008-11-03
> **hanzomon4 said:**
> How do I set the screen and keyboard backlight to be controlled by ambient light like in OS X?
I'd start off by checking this:
[https://help.ubuntu.com/community/MactelPPA](https://help.ubuntu.com/community/MactelPPA)

---

### Post by kosumi68 on 2008-11-03
> **hanzomon4 said:**
> How do I set the screen and keyboard backlight to be controlled by ambient light like in OS X?

As cyberdork pointed out, the package hal-applesmc has support for both keyboard backlight and light sensor. However, the light sensor settings are commented out in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi, because of known problems with unstable light control [1]. It is still included for anyone who wants to test it :-)

If you do get it to work nicely, please report, and I'll include any necessary changes in the package.

[1] [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815)

---

### Post by hanzomon4 on 2008-11-03
What should I change in that file? Not use to XML.

---

### Post by Nikos.Alexandris on 2009-07-30
Just out of curiosity, has anyone played around with values for the light sensor(s)?

---

