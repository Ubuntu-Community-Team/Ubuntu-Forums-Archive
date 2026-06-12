---
title: "usb devices not showing up in feisty upgrade"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-05-05
In my edgy installation, usb devices appear in /dev/ttyUSB0 /dev/ttyUSB1 etc.  Now that I installed feisty I dont see ttyUSB anything.  Please help.

---

### Post by gradedcheese on 2007-05-05
What kind of device?  /dev/ttyUSBx is for "USB to Serial" adapters, ie: ones that provide a serial port.  Any other kind of device will have a different device name.  That said, in Feisty you need to:

```

sudo apt-get remove brltty brltty-x11

```

because it grabs the USB serial devices when it shouldn't.  Do that, reboot, and you'll see them show up again.  I (and others) have reported this problem but the bryltty people thing it's a HAL problem.  it sort of is, but the reality is that they shouldn't be doing this...

---

### Post by outer_space on 2007-05-05
I tried that and still no ttyUSB devices.  But I found a possible answer to my main problem of ttyACM0 version disconnecting all the time.

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)
suggests adding these lines:
lcp-echo-failure 0
lcp-echo-interval 0
"The script above copes with a problem I initially had of the connections were being terminated after a couple of minutes"

---

### Post by gradedcheese on 2007-05-05
Check dmesg output, on Feisty you will likely find that brltty grabbed the device before the driver could.  If that's not the case, you should at least see what else is going on.

---

### Post by outer_space on 2007-05-05
Adding those lines to /etc/wvdial.conf didnt work.  heres lines from dmesg that show how it ends up as ttyACM instead of ttyUSB

[  206.424000] cdc_acm 3-1:1.0: ttyACM0: USB ACM device
[  206.428000] usbcore: registered new interface driver cdc_acm
[  206.428000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

Before on edgy the phone shows up as a samsung z100 on ttyUSB, on feisty the phone shows up as samsung CDMA without specifying a model and on ttyACM.  It works great on edgy and disconnects every 2 minutes on feisty.

Heres what it says when it disconnects

--> Disconnecting at Sat May  5 20:59:13 2007
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)

---

### Post by outer_space on 2007-05-05
Adding these lines to /etc/ppp/peers/wvdial appears to have fixed my disconnecting problem.

lcp-echo-failure 4
lcp-echo-interval 65535

And it only took me 4 hours to fix!  Still no ttyUSB devices but i can worry about that later.

---

