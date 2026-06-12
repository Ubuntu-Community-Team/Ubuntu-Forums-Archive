---
title: "A few problems with 9.10 on MBP 5,1"
date: 2009-10-08
forum: Apple Hardware Users
---

### Post by mvh on 2009-10-08
Hi,

Just upgraded to 9.10 and I have a few problems:

When I boot with kernel 2.6.31-12 the screen starts to flicker at the point where it says:
* Setting preliminary keymap
* Starting AppArmor profiles
etc...

the boot continues fine however after a while and I get to GNOME fine. The next problem is that I can't get the sound to come out of the headphone jack. It works fine from the built-in speakers, but not from the headphones. There seems to be no way of adding output devices in the sound preferences.

There's no flickering with kernel 2.6.28-15 but the sounds don't work at all.

Any help would be greatly appreciated. Thanks!

---

### Post by Niels den Otter on 2009-10-08
I have the same problem. A workaround is to use the Gnome Alsa mixer and lower the 'master volume' to silence the speakers and higher the 'hp' (headphone) volume to use the headphone output.

Not optimal, but works for me.


-- Niels

---

### Post by mvh on 2009-10-08
Hei thanks, that's what I was looking for! Another thing that changed was that I can't rotate the Compiz Cube with the mouse wheel anymore, any workarounds for that? Thanks!

---

### Post by elitenoobboy on 2009-10-09
> **mvh said:**
> Another thing that changed was that I can't rotate the Compiz Cube with the mouse wheel anymore, any workarounds for that? Thanks!

They specifically disabled that in karmic. You can install the compiz settings manager and then reenable it from the viewport switcher plugin, IIRC.

---

### Post by alexmurray on 2009-10-09
Also the flickering is not a bug, thats how it is in Karmic with proprietary nvidia drivers that dont do kernel mode setting... shame, but its not such a big loss.

---

