---
title: "Need help with ndiswrapper"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Westies on 2006-12-19
I'm using a D-Link DWL-G122 Rev B1 usb nic. I've been having some wifi issues, so I figured I should try using the windows drivers with ndiswrapper. I got ndiswrapper to install the drivers and run at bootup, however, it doesn't load the drivers for the nic. Instead, I think the drivers that came with edgy are being used still.

ndiswrapper -l displays:
netrtusb : driver installed
device (2001:3C00) present (alternate driver: rt2570)

the system log at bootup shows

dmesg shows:

[17179629.300000] rausb1: no IPv6 routers present
[17180128.064000] usbcore: deregistering driver ndiswrapper
[17180143.732000] ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
[17180143.736000] usbcore: registered new driver ndiswrapper

But nothing of ndiswrapper loading drivers for the rausb1 device. The only other place rausb1 shows up is "[17179612.392000] rausb1 (WE) : Driver using old /proc/net/wireless support, please fix driver !"


So, how would I go about making Ubuntu using ndiswrapper?

edit: After doing an apt-get install ndisgtk, doing a ndiswrapper -l now tells me:
"Installed ndis drivers:
netrtusb        driver present, hardware present "

Why would installing this package change that? As far as I can see in dmesg, nothing has changed.

---

### Post by Westies on 2006-12-19
How can I blacklist the default driver so that it has to use ndiswrapper?

---

### Post by Westies on 2006-12-19
One last bump.

---

