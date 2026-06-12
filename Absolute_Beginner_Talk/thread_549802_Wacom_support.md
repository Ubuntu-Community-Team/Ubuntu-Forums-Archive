---
title: "Wacom support?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by frith on 2007-09-13
I'm wondering if anyone there can give me some pointers regarding wacom drivers... I'm using a toshiba m200 tablet.

When I first install Feisty, the stylus worked. Now it doesn't. My xorg.conf is in the default state (using sudo blah -phigh blah...)

In my xorg.conf the stuff for the wacom drivers is there. Its got the corret /dev/input/wacom lines. The stylus just doesn't work... Also, when i do sudo wacdump /dev/input/wacom it says there is no device.

If you look here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646)

There is a list of stuff this other person did. I did the same thing with (predictably) the same results - it seems to all be installed, it just doesn't work.

Can anyone offer some insight? It feels like I have searched high and low for the answer, but its not forthcoming...

Frith.

---

### Post by slimdog360 on 2007-09-13
you might want to give ubuntu studio a try, I read somewhere it comes with support already set up for that sort of stuff.

---

