---
title: "G73SW power manager on close lid &quot;do nothing&quot; broken"
date: 2011-11-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by l0r3zz on 2011-11-01
Running 11.10 on a new G73SW. Running dual monitors but disabling the laptop monitor (using 28" Hanns-G HDMI as main and only monitor). I've tried to set the power manager to do nothing when the lid is closed, but it still seems to blank the screen or maybe even attempt a suspend, in any event, the system has to be rebooted after I attempt this.

Any Ideas?

Asus G73SW
16 GB RAM
120 GB MAX IOPS SSD
Nvidia GeForce GTX-460M

---

### Post by l0r3zz on 2011-11-02
This is [SOLVED]. This is what I did ...
[B]
sudo gconftool-2 -t string -s /apps/gnome-power-manager/buttons/lid_ac nothing[/B]

Then closing the lid did blank the screen, but after several seconds the external monitor came back on.  I'm not sure if this command actually changed the behaviour or not but it was one of the steps that  I applied.

---

### Post by Cardale on 2011-12-11
How is your display?  Do you have any glitchy or laggy windows when moving them around the screen?  I have the same laptop.

---

