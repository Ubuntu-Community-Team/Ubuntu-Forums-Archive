---
title: "Mounting USB-sticks?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Ba|der on 2006-10-22
I have 4 differnt USB sticks, but one of them is automounted by Ubuntu (It's a 1 Gb Kingston DataTraveler Elite stick) How do I mount the other sticks?
```

cat /var/log/syslog
[...]
Oct 22 20:30:42 localhost kernel: [17210302.696000] usb 2-1: new full speed USB device using uhci_hcd and address 24
Oct 22 20:30:46 localhost kernel: [17210306.728000] usb 2-1: new full speed USB device using uhci_hcd and address 25
lsusb does not show my units, except the Kingston unit and the Trust (which works with the microphone)
Kingston unit is shown as:
Bus 003 Device 023: ID 08ec:0015 M-Systems Flash Disk Pioneers

```

The names of the other units that works fine as usb-sticks in Windows 2000 is:
1. TyniDisk 32MB
2. Microdia.com Compact flash (TM) Card reader, Model: iFlash CF-Direct Card Reader (with a Kingston 1024Mb CF)
3. Trust Camera with a Kingston 1024Mb CF)

---

