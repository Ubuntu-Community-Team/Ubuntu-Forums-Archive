---
title: "MacBook Pro Mid 2012 b43 (4331) wifi disconnects"
date: 2013-01-21
forum: Apple Hardware Users
---

### Post by IanBlanes on 2013-01-21
I just wanted to let you know that if you are having wifi problems with a Broadcom 4331 chip (MacBook Pro 9,2 / Mid 2012) you might want to use the following options for the b43 module:

nohwcrypt=1 qos=0

(It takes a few weeks to test conclusively, so I haven't checked if individually either option is enough)

You can place them in a file like /etc/modprobe.d/b43.conf with:

options b43 nohwcrypt=1 qos=0

and then update your initramfs (update-initramfs -u).

You got them working if you see "b43-phy0 debug: QoS disabled" in your dmesg when you employ also the "verbose=3" option.

---

### Post by thinlizzy78 on 2013-01-22
regarding different forums, many people have this problem and i'm one of them.
the problem appears in both Ubuntu and MacOS. is it only a firmware problem or is it a hardware problem?
i will try your solution later today.

---

### Post by Benjamindaines on 2013-02-10
I don't want to speak too soon, because I know as soon as I post this reply I'll start having problems.  However, this seems to have solved my wifi problems.  Previously, I was having trouble with my card dropping out when switching between access points on my school's network.  Now my transfer rates see much better, and I've successfully be switched to another AP without losing connection.  Thanks!  This really needs to be in a wiki somewhere, I spent many days searching google before I found this.

I'm running kubuntu 12.10 on a MacBook Pro 8,2 with the same BCM4331 card.

EDIT: Didnt work.

---

