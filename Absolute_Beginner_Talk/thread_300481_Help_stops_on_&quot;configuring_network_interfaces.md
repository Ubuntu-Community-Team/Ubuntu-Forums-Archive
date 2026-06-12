---
title: "Help stops on &quot;configuring network interfaces&quot;!"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-11-15
Help every time I boot my computer (just installed) it stops on "configuring network interfaces", I am LOST on what just happened, I need help as that is the computer that I do most of my work on!](*,)

---

### Post by Phalangees on 2006-11-22
i have the same problem. i can't do anything to get onto the computer. it was working fine. please someone help. i'm using edgy 6.10

---

### Post by Peepsalot on 2006-11-22
Maybe your interfaces file( /etc/network/interfaces ) is not configured right.

You might have to use a liveCD in order to boot and mount the drive for the file viewing/editing.

If you can, post the contents of that file up here.

You might also try looking through your logs.  The command dmesg will give you some boot messages that might help pinpoint the problem, and the log file /var/log/dmesg has some more info.  I still haven't figured out the difference in these two :-?.

---

### Post by Frak on 2006-11-22
Press ctrl+c to skip it then go into the interfaces file to edit it. No liveCD needed.
EDIT
Plus I found my problem, Ubuntu wouldn't work on my desktop, but Kubuntu did, go figure.
Thats vice versa on my laptop.

---

### Post by Phalangees on 2006-11-22
ctrl+c doesn't do anything.

the interfaces file located at /etc/network/interfaces contains

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




this is the weird part though. I just put in a new video card because anytime anything tried to access OpenGL ubuntu would restart. I boot up with the card and it hangs at configuring network interfaces. Pop the card out and use the integrated and it won't work. i'll post the contents of the interfaces file with the card later but i have to go to work and don't have time to wait for the liveCD

---

### Post by Peepsalot on 2006-11-23
> **Phalangees said:**
> ctrl+c doesn't do anything.

the interfaces file located at /etc/network/interfaces contains...

Back up this file, and try removing all the lines besides the ones for "lo" and "eth0".   This would be assuming you have only one single (non-wireless)network card.

---

