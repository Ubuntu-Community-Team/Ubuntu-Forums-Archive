---
title: "problems with ndiswrapper / WUSB11v2.6"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2008-01-04
I installed ndiswrapper and the drivers for my Linksys WUSB11v2.6 adapter.  ndiswrapper -l was showing ```
netusb : driver installed
        device (077B:2219) present (alternate driver: at76_usb)

```

I blacklisted at76_usb, and rebooted.  It appears that ndiswrapper is not loading at startup.  There is no mention of it in the system log, and the usb adapter is not being found.  ndiswrapper -l still gives the same message...

What gives?

---

### Post by lswest on 2008-01-04
try running ```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
``` in the terminal and in /etc/modules (open with ```
gksudo gedit /etc/modules
```) add ndiswrapper to the file.  should start up at boot then.

---

### Post by vojtech.t on 2008-01-04
Have you added ndiswrapper into /etc/modules ?

---

### Post by cifdtruckie on 2008-01-04
Tried that - it seemed to work, but then after about 30 seconds the system hard-crashed.  When I hard-rebooted, the adapter was not found:

```
chris@chris-desktop:~$ iwconfig wlan0
wlan0     No such device

```

---

### Post by vojtech.t on 2008-01-04
Are you sure, that the device is wlan0? Try "iwconfig eth1".

---

### Post by cifdtruckie on 2008-01-04
Nothing... here's the entire iwconfig:

```
chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

wlan0 was showing up before the hard-crash...

I did find the following in the system log:
```
Jan  4 14:11:03 chris-desktop kernel: [   36.215734] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
Jan  4 14:11:03 chris-desktop kernel: [   36.215739] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jan  4 14:11:03 chris-desktop kernel: [   36.215748] ndiswrapper (mp_halt:259): device dfb5c500 is not initialized - not halting
```

I'm also still seeing the at76_usb driver when I run ndiswrapper -l, even though it's blacklisted...

---

### Post by lswest on 2008-01-05
ndiswrapper usually renames the card wlan0.  make sure the blacklist changes were saved in the file.  and i don't believe ndiswrapper -l will stop displaying the alternate driver as long as that driver is installed.  if it's blacklisted, it shouldnt be running.

---

