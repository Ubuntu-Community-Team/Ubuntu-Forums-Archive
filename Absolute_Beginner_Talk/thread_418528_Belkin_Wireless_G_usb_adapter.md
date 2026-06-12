---
title: "Belkin Wireless G usb adapter"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-04-22
I upgraded to Feisty from Edgy and have been plagued with problems. Edgy worked flawlessly for me, but now: a partition in my hard drive wouldnt mount, but I managed to fix that, my nvidea driver wasnt working  so im now using non-3d nv. Now for my final problem, my wireless internet adapter has stopped working. It's a BELKIN Wireless G USB Network Adapter, the model number is F5D7050. If i plug it in and run dmesg, here's what I get:
```
[ 4155.512000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 4155.844000] usb 1-1: configuration #1 chosen from 1 choice
[ 4156.560000] Loading module: rt2x00lib - CVS (N/A) by http://rt2x00.serialmonkey.com.
[ 4156.584000] Loading module: rt73usb - CVS (N/A) by http://rt2x00.serialmonkey.com.
[ 4156.848000] usbcore: registered new interface driver rt73usb
[ 4156.876000] usbcore: registered new interface driver prism54usb
[ 4156.908000] usbcore: registered new interface driver rt2570
[ 4157.560000] wmaster0: Selected rate control algorithm 'simple'
[ 4157.672000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -32.
[ 4157.864000] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 4157.868000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.872000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.880000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.884000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.888000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.892000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.900000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.904000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.908000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.912000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.920000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.924000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.928000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.936000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.940000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.948000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.952000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.956000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.960000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.968000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.972000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.976000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.984000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.988000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.992000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4157.996000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.004000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.008000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.012000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.016000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.024000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.028000] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 4158.032000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.072000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -32.
[ 4158.084000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.088000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.096000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.100000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.104000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.108000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.116000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.120000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.128000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.132000] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 4158.136000] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 4158.144000] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
[ 4158.148000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.152000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.156000] rt73usb->rt2x00_bbp_write: Error - PHY_CSR3 register busy. Write failed.
[ 4158.200000] wlan0: starting scan

```

---

### Post by goodbyewindows on 2007-04-25
Anybody?

---

### Post by Bachstelze on 2007-04-25
Drivers error, most likely. How did you install them ?

---

