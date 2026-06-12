---
title: "Mint Linux 14"
date: 2013-06-01
forum: Any Other OS
---

### Post by gordie69 on 2013-06-01
Hey guys I put mint 14 on a friends laptop and everything works great he's very happy he's like me no more Windows but on the laptop the web cam is not showing in the system settings when you go to sounds and input you see your web cam but he doesn't is anything I didn't do or something from terminal

---

### Post by craig10x on 2013-06-01
Install the program called Cheese...that should put it on, hopefully...worth a shot, anyway...

---

### Post by tgalati4 on 2013-06-01
Open a terminal:

```
lsusb
```

It might look like:

tgalati4@Mint14-Extensa ~ $ lsusb
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye **Webcam**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If you don't see webcam then it is not being detected.

---

### Post by gordie69 on 2013-06-01
Thanks I'll try cheese

---

### Post by craig10x on 2013-06-01
My experience has been that if you install Cheese and the webcam doesn't immediate come on when you open the program, that you will probably not get the webcam to work on that distro/version...
Perhaps others will come along with a different experience....

Just out of curiosity, i installed Cheese and my webcam came right on....i am using Ubuntu 13.04 so it seems to work on that...Mint 14 is based on 12.10...also, mint make modifications to ubuntu which sometimes affect certain things...best way to check is to run a live iso, install Cheese and check it...so, for example, you could check Mint 15 iso and then Ubuntu 13.04 and see if it works on those...

---

### Post by gordie69 on 2013-06-01
thanks craig 10x I cheese is pre installed but didn't detect in the sound input but the code lusb how do install it though terminal

---

### Post by tgalati4 on 2013-06-01
*lsusb* is a utility, it does not require installation.  That's an L not an I.

---

### Post by gordie69 on 2013-06-01
how do I use the L usb

---

