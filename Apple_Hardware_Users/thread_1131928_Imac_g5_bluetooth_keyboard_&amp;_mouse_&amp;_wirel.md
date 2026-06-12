---
title: "Imac g5 bluetooth keyboard &amp; mouse &amp; wireless"
date: 2009-04-21
forum: Apple Hardware Users
---

### Post by Colinwlu on 2009-04-21
Hi

I have just updated from 8.04 to 8.10 and now my Apple bluetooth keyboard & mouse only work if I restart bluetooth from the terminal:-
 sudo /etc/init.d/bluetooth restart
I need a usb keyboard (which I have borrowed) but this kind of defeats the object.
Anyone got any ideas. 

Also cannot connect to the internet using wireless, only ethernet.
I have an Apple Extreme card BCM4306 Rev 03.
I thought updating to 8.10 might cure this but it hasn't.
Any ideas on this please. 
Clear advice please as I'm a novice using Terminal.

Colin

---

### Post by Colinwlu on 2009-04-22
Right or wrong, I've managed to get my bluetooth mouse and keyboard to work from boot up.
In  /etc/default/bluetooth, I disabled bluetooth, ie BLUETOOTH_ENABLED=0.
I don't know why but it works. Set up new devices doesn't work but I don't need to set anything else up. I can gratefully return the borrowed usb Keyboard & mouse. 
Hope this helps others with the same problem but if anyone knows a better way I'd be grateful.
Now to get wireless internet to work.

Colin  :P

---

### Post by tiresia on 2009-04-22
I can't help you about bluetooth - anyway it looks that you found a way.
About wireless: Broadcom should be the manufacturer of the Apple Airport Extreme wireless chip.
Check it ```
lspci | grep -i broadcom
```
If it's so you need to install the b43-fwcutter
```
sudo apt-get install b43-fwcutter
```
After that, reboot and make sure that the module 43 is loaded

Actually, in Ubuntu, you should be able to install it also with System > Administration > Hardware Drivers

---

### Post by Rhubarb on 2009-04-22
The reason why upgrading from Ubuntu 8.04 to 8.10 introduces problems with bluetooth, is because the main bluetooth library for them have different package names (and probably features too).

As you can see here for 8.04:
[http://packages.ubuntu.com/hardy/libs/libbluetooth2](http://packages.ubuntu.com/hardy/libs/libbluetooth2)

Here for 8.10
[http://packages.ubuntu.com/intrepid/libs/libbluetooth3](http://packages.ubuntu.com/intrepid/libs/libbluetooth3)

A clean install of 8.10 (or 9.04 that'll come out really soon) should fix any bluetooth issues.

---

### Post by Colinwlu on 2009-04-22
Rhubarb, as bluetooth is working for me I'll leave well alone for now but thanks for the advice.
Tiresia, I followed your advice and typed in the first code:-

 lspci | grep -i broadcom
0001:01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:02:0c.0 IDE interface: Broadcom K2 SATA

I then installed b43-fwcutter as suggested but it appears to be already installed:-

sudo apt-get install b43-fwcutter 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-image-2.6.24-19-powerpc64-smp
  linux-ubuntu-modules-2.6.24-23-powerpc64-smp binutils-static
  linux-restricted-modules-2.6.24-23-powerpc64-smp
  linux-restricted-modules-2.6.24-19-powerpc64-smp
  linux-restricted-modules-powerpc64-smp linux-restricted-modules-common
  linux-ubuntu-modules-2.6.24-19-powerpc64-smp
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I've entered my isp details in System>Preferences>Network Configuration but when I 
click the  Network icon (top right), Wireless Networks is greyed out.
Is there another file that needs to have wireless enabled (or disabled as was the case with bluetooth)? :P

Thanks
Colin

---

### Post by tiresia on 2009-04-22
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by Colinwlu on 2009-04-23
I decided to do a clean install of 8.10 as suggested by Rhubarb. This made no difference to bluetooth or wireless.  Shortly after installing, it updated with over 900 files & then said an ugrade to 9.04 was available. I let it run the upgrade and received all sorts of errors at the end but it has updated to 9.04. During the install it said I needed b43-fwcutter.  This however failed to install for some reason. I couldn't even send a bug report as that failed also.  I managed to download it from terminal and it appeared to install OK, however I still can't connect wirelessly.
Bluetooth still only works with the fix I did before. Doesn't look like 9.04 is any benefit iMac G5 users. :(

Colin

---

### Post by Colinwlu on 2009-04-23
I take back my last remark.  I've just restarted my iMac and it has found my wireless network. Guess it takes a few restarts to kick it into gear. Just hope it lasts!
Thanks

Colin :D

---

### Post by stream303 on 2009-04-24
Glad to hear that's working out for you.  9.04 is doing fine on my G5 iMac, although with the 20" screen, the nv driver needs to be recompiled to fix the slight amount of screen offset (it's a driver issue, not an xorg issue)

You may want to keep a cheap usb keyboard handy in your toolbox just in case, so you don't run into that catch-22 if/when you need to reinstall or boot up a rescue disk by holding down the "C" key. :)

In fact, on my system, I run a Microsoft usb-keyboard and Microsoft 3-button scrollwheel mouse without any problems - other than just being too lazy to reprogram the media keys to do something useful. :)  But, just wanted to point out that one isn't limited solely to Apple keyboards and mice...

---

### Post by cyberdork33 on 2009-04-24
> **stream303 said:**
> In fact, on my system, I run a Microsoft usb-keyboard and Microsoft 3-button scrollwheel mouse without any problems - other than just being too lazy to reprogram the media keys to do something useful. :)  But, just wanted to point out that one isn't limited solely to Apple keyboards and mice...
Yea I can't stand the mighty mouse... I have been using a MS Intellimouse Optical for years... I love it. (I have more than one).

---

### Post by Colinwlu on 2009-04-24
Thanks for the advice but use something by microsoft...............yuk.:mad:
I have an Apple computer because I refuse to help bill gates get richer.
I will however look out for a usb keyboard & mouse on ebay or somewhere.
:-D

Colin

---

### Post by cyberdork33 on 2009-04-24
Logitech makes good hardware too.

---

