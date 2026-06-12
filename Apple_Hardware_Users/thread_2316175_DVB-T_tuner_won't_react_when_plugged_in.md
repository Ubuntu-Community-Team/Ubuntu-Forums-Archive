---
title: "DVB-T tuner won't react when plugged in"
date: 2016-03-05
forum: Apple Hardware Users
---

### Post by zemko on 2016-03-05
Hi, I migrated from my old Lenovo to Macbook Pro (2015, Retina). Almost everything is working fine, but what concerns me most is my DVB-T Tuner.

According to lsusb it is: 04ca:f000 but in the Lenovo laptop it was showing as 04ca:f001 (branded version of the previous). If I use same set up method as before ([http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Supported_by_3rd_Party_Drivers](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Supported_by_3rd_Party_Drivers)) the problem still persist, in the lsusb I can see that this device is plugged in, but in Me-TV it shows me that no DVB-T device was found. LED diode on the tuner won't even light up.


The firmware from the site is in /lib/firmware - same directory as in the lenovo; I tried the /usr/lib/firmware but without any positive result.

The only difference is that on Lenovo is 15.04 and on Macbook I have 15.10.

Can someone help?


Thanks

---

### Post by Linuxisfast on 2016-03-05
I have done Intel to AMD motherboard and CPU change without any issues. I made sure all proprietary drivers were removed as well as Intel microcode and Thermald. After booting just did AMD specific installs and drivers, absolutely no issues.

---

### Post by zemko on 2016-03-06
Linuxisfast: I'm sorry, but I don't get your point

update: I tried different DVB-T tuner 048d:9135 and it is working fine (when it is directly in the USB port, not connected through extended USB cable), according to the list of DVB-T sticks, this DVB-T dongle is supported from later version of kernels, so it is even more odd, that the 04ca:f001/f000 is not working

---

### Post by howefield on 2016-03-06
Moved to "*Apple Hardware Users*" forum.

---

