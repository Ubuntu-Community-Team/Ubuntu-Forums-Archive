---
title: "USB wifi adaptor trouble"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by infinitewisdom on 2007-02-12
I have what I am pretty sure is a Net-Lynx WU61S usb wifi adaptor 54 mbps. When I plug it into my usb port it doesnt light up at all and does not appear in device manager. I know the port is working and the adaptor is working as I use it on my adjacent xp machine. I have just reinstalled 6.06 and are a novice at using linux. How would I get Ubuntu to recognise this device as I cant locate a driver for it other than the windows variety? Is there a simple way to connect my network port directly to my other pc simply to access the web, I dont need any other advanced features. Any help or links appreciated.

---

### Post by %hMa@?b&lt;C on 2007-02-12
> **infinitewisdom said:**
> I have what I am pretty sure is a Net-Lynx WU61S usb wifi adaptor 54 mbps. When I plug it into my usb port it doesnt light up at all and does not appear in device manager. I know the port is working and the adaptor is working as I use it on my adjacent xp machine. I have just reinstalled 6.06 and are a novice at using linux. How would I get Ubuntu to recognise this device as I cant locate a driver for it other than the windows variety? Is there a simple way to connect my network port directly to my other pc simply to access the web, I dont need any other advanced features. Any help or links appreciated.
is it detected at all?
after plugging it in, type  in terminal
```
dmesg |tail
```
and
```
lsusb
```

---

### Post by teaker1s on 2007-02-12
yes terminal and type
[COLOR="Red"]lsusb[/COLOR]

thats a small L not i

---

### Post by infinitewisdom on 2007-02-13
The adaptor is not detected at all. lsusb brings up 5 device adresses, all blank and one which describes the integrated usb maker. The dmesg command displays an error as though the command is not recognised.

---

