---
title: "Why aren't my USB devices being recognized?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by hugotaem on 2008-04-01
Hello,

Suppose I install a brand new Ubuntu (2.6.24-12-generic) from CD, and everything seems to work perfectly fine, is there anything that needs to be done in order to enable the USB ports? I tried a Sierra USB modem, three different memory sticks, and a USB mouse, but Linux is not reacting to any of this, while both MacOS X and Windows XP recognize them all. I thought is would automatically be made available in Linux too...

Is there anything that needs to be done after a first Ubuntu installation to enable USB?

When I type "lsusb", it just displays:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

... and this info never changes, no matter what device I plug in which USB port.

When I type "lsmod | grep usb", it displays:

usbserial    35816   1 sierra
usbcore     146028  5 sierra,usbserial,ehci_hcd,uhci_hcd

And "lspci" displays me four times something like "00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/IHC4-M) USB UHCI Controller #1 (rec 01)"

Cheers,
Hugo

---

### Post by Matthewslf on 2008-04-01
The mouse and memory sticks suprise me. Those should work. As for the modem, you will probably need special drivers for it.

Use the restricted drivers manager first, and if that doesn't work, look at this:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601")

---

### Post by hugotaem on 2008-04-04
Problem "solved".
It was defect hardware :(

---

