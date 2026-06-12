---
title: "Keyboard Backlight on Powerbook G4"
date: 2011-03-10
forum: Apple Hardware Users
---

### Post by stuffelse on 2011-03-10
Hello all,

Just acquired a retired Powerbook G4 from work, and threw 10.04 LTS PPC on it. So far everything's working great, but I can't get the backlighting working on the keyboard.

I've tried installing pommed 1.31 and 1.2 according to a few posts I found on here from searching, but neither seems to work. I know the keyboard hardware works, because it was functional in OSX before I wiped the drive.

Anybody got any ideas, or remember fighting with this on their own p-p-powerbook?

---

### Post by linuxopjemac on 2011-03-10
which version of pommed do you use?

---

### Post by alexmurray on 2011-03-10
Does the file /sys/class/leds/smc::kbd_backlight/brightness exist?

If so you can enable keyboard brightness control via gnome-power-manager and upower by using [my ppa]("https://launchpad.net/~alexmurray/+archive/ppa").

This should work out of the box with natty [with any luck]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/724324")

---

### Post by stuffelse on 2011-03-11
> **alexmurray said:**
> Does the file /sys/class/leds/smc::kbd_backlight/brightness exist?

If so you can enable keyboard brightness control via gnome-power-manager and upower by using [my ppa]("https://launchpad.net/~alexmurray/+archive/ppa").

This should work out of the box with natty [with any luck]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/724324")

I don't know about that file, I'll have to check when I get back to the computer.

Unfortunately, I think this project might be backburnered, or abandoned, given the fact that there's no Flash player and Java is kinda tricky for PPC...

---

