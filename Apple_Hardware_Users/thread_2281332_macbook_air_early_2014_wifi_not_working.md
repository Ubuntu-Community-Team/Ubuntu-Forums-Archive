---
title: "macbook air early 2014 wifi not working"
date: 2015-06-06
forum: Apple Hardware Users
---

### Post by tim120 on 2015-06-06
Today i installed ubuntu alongside os x, and it worked but the problem is that the wifi does not work. it does not find any wifi. 
Do i need to install a driver for my wifi card or something? 
i dont have a cable to plug straight into the internet though, so can i install it on another computer and put it on a usb?
Thanks

---

### Post by rican-linux on 2015-06-06
You will need a usb-ethernet adapter then plug to your router. then i think under software updates you should wifi driver listed with additional drivers.

---

### Post by Amit_Prabhakar on 2015-06-14
You may save some money by taking the packages from the ISO. 

Assuming you have a Broadcom hardware - which is a good assumption as I have the same model (early 2014) and I have a Broadcom4360 chip -  after you confirm that, *bcmwl-kernel-source* is correct for your device. A confirmation can be done like this:

```

lspci -nn |grep 14e4
02:00.0 Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

```



If you you don't have any internet connection, you might still install it and the method is very simple. For doing that, mount the ISO (use *mount -t*), if you have the ISO of the installer image. Navigate to these two folders  and drag and drop the two deb packages inside them to your desktop.


[LIST=1]
[*]pool > restricted > b > bcmwl 
[*]pool > main > d > dkms 
[/LIST]
 


Open up a terminal, Issue a command to install these two packages.

```
cd Desktop
dpkg -i *.deb
```

There is a small twist here. The package provided by the ISO is a bit old. It might not work as it did not for me. You may downloaded the updated package from internet and install. This works without a problem.

It should be *6.30.223.248+bdcom-0ubuntu1*, hwoever the ISO provides you with *6.30.223.141+bdcom-0ubuntu2* which is a bit older. The newer package can be got from here - [http://packages.ubuntu.com/utopic/bcmwl-kernel-source](http://packages.ubuntu.com/utopic/bcmwl-kernel-source) 

Once done you may load your module with a restart.
```
sudo modprobe wl
```

Works like a charm! 

P.S. My kernel version is *3.16.0-30-generic* (you may know yours by typing *uname -r* at your terminal in ubuntu).

---

