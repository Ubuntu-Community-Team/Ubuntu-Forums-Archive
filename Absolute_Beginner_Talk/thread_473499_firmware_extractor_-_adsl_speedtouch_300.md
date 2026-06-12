---
title: "firmware extractor - adsl speedtouch 300"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2007-06-14
Hello ,newbie here ,i'm following the instructions to install my adsl modem here:

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

I'm stuck with what to do with the firmware-extractor. It says "download the frimware extractor from here:

[http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor)

but this just gives me a page of code. Would someone explain my next step please.

My broadband supplier only supports windows and macs...


completed so far :

pete@MyPlace:~$ grep -B 1 "THOMSON" /proc/bus/usb/devices
P:  Vendor=06b9 ProdID=4061 Rev= 4.00
S:  Manufacturer=THOMSON
pete@MyPlace:~$ 

pete@MyPlace:~$ cd speedtouch
pete@MyPlace:~/speedtouch$ dir
KQD6_3.012  SpeedTouch330_firmware_3012.zip  ZZZL_3.012
pete@MyPlace:~/speedtouch$ 

I'm writing this via 'xp' ,hope to be able to write via unbutu soo !


Pete

---

### Post by candtalan on 2007-06-15
when I (left) click on your  link
[http://www.linux-usb.org/SpeedTouch/...ware-extractor](http://www.linux-usb.org/SpeedTouch/...ware-extractor)
(using firefox browser) I get a window appear saying it is a binary file and do I want to run it or save it somehwhere?

I would save it and then the next step would be to use it (according to your instructions - 
(?install it ? or run it somehow??)

If you have to run it, then first you need to alter its properties to make it allowed to execute - become an exectutable.

hth

---

