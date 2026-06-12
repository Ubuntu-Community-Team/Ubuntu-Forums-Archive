---
title: "Blue Tooth.."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by nconceicao on 2007-08-04
Hello Everyone,

I have been going nuts trying to configure bluetooth on my laptop..
I follow the correct instructions and have read many posts..

The installation process seems to work..

Ubuntu 7.04

When I open a terminal window and list the devices it does not seem to see the Bluetooth as a device or MAC. as being installed?

Any references tor recommendations?

thank You

---

### Post by nconceicao on 2007-08-04
On a different topic anyone able to sync up a Sony Ericson bluetooth phone sucessfully with ubuntu??

I still need blue tooth to work?

---

### Post by linuxwizard on 2007-08-04
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by MrFSL on 2007-08-04
> When I open a terminal window and list the devices it does not seem to see the Bluetooth as a device or MAC. as being installed?


are you typing:
```
sudo hcitool dev
```

Is your bluetooth adapter internal? USB?

---

### Post by nconceicao on 2007-08-04
Internal 

Devices:
Lists NIC
Modem

but no blue tooth..

I will try to take screen shots no laptop with me today.

---

### Post by nconceicao on 2007-08-06
here is the information bellow? any ideas?

xxx@xxx-laptop:~$ sudo /ect/init.d/bluetooth restart
sudo: /ect/init.d/bluetooth: command not found

xxx@xxx-laptop:~$ sudo /ect/init.d/bluez-utils restart
sudo: /ect/init.d/bluez-utils: command not found

xxx@xxx-laptop:~$ sudo /ect/init.d/bluetooth restart
sudo: /ect/init.d/bluetooth: command not found

xxx@xxx-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by skidkid87 on 2007-08-08
I have the same problem with my sony ericsson phone, I can't seem to be able to send files from my mobile to the laptop, a bluetooth aplication called "bluetooth obex" client works for sending files the other way around

---

### Post by philinux on 2007-08-08
MY K810i works fine, after installing blue tooth chat and obex client. However I connected my phone with the usb cable fired up Gthumb and there was the phone and phone card like a device. It's a faster transfer rate too.

---

### Post by nconceicao on 2007-08-08
The problem I am having is I can't seem to get my bluetooth to work on my laptop with windows it works perfectly on unbuntu does not see the device.. no diea what else to try, anyone have any ideas? 
Built on Toshiba..

---

