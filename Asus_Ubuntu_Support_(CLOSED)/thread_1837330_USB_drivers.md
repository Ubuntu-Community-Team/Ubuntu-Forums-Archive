---
title: "USB drivers"
date: 2011-09-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by laytek on 2011-09-01
Hello,

The problem: my Asus M4A88TD-V EVO/USB3 motherboard (updated to the 1201 BIOS) is described as having 12 ports x USB 2.0 and 2 ports x USB 3.0. However, a lsusb listing shows:

Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Why are buses 4, 5, 6, and 7 showing as USB 1.1? Does the ID column indicate three different controllers?

I am using Ubuntu 10.04.3 LTS. Thanks for any help.

LayTek

---

### Post by laytek on 2011-09-05
Any ideas? I keep thinking that BIOS is not reporting correctly as the OS loads, but have not had any success when I change the USB options.

Laytek

---

### Post by jmate24 on 2011-09-09
is it a laptop or desktop? if it is a desktop then you have a special connector on the motherboard for your front usb it is usually usb1.1.

---

### Post by laytek on 2011-09-10
Thanks jmate.

This is a desktop system that I built. There are 4 headers on the motherboard to connect the front panel USB outlets. I have experimented with two of the four, with no changes noted. All four are documented as USB 2.0 ports.

I am still working with the idea that the BIOS is reporting legacy controllers to the OS during boot.

Laytek

---

### Post by UnoSD on 2012-03-16
I have this problem too, also the same board (Asus M4A88TD-V EVO/USB3).

Can please someone help us?

---

