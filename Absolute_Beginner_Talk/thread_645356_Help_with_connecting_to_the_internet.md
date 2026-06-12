---
title: "Help with connecting to the internet"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by KadFlynn on 2007-12-20
Hey guys. I'm completely new with this and I'm not all that computer savvy (I'm learning though). I was working with a friend on getting my computer connected to the internet, and it works. My techie friend said the drivers were working, it just wasn't connecting. I wasn't so sure, myself..... I heard Broadcom internet cards didn't work so well with linux...

We went to the network area, and clicked on wirless connection. Even now it says that it's connected to my router. But I cannot access the internet. Any help would be gladly appreciated.

My internet card is a Broadcom BCM94318MPG (802.11b/g) and my router is a Belkin. It worked fine when I used windows, so I know everything works. 

Thanks in advance!

---

### Post by Severun on 2007-12-20
I've got a broadcom card in my laptop

lspci shows it as

 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)


In order to get it to work I had to use the Intel PRO/Wireless 3945 Driver

In order to get it installed I had to install the restricted modules.  If you use the Synaptics Package manager and search for restricted you should see them.  Then you can use the Restricted driver manager to enable the driver.

System->Administration->Restricted Drivers manager.

Also of note, is when you upgrade, it will disable restricted drivers so you have to re-install them after an upgrade.

---

### Post by willie_wang on 2007-12-20
Yeah, if the bundled restricted driver doesn't work, then try downloading the windows driver and using the ndiswrapper package (available in synaptic) with the windows driver. You can get the windows driver from your notebook manufacturer's webpage.

Now navigate to the folder where you downloaded the windows driver. Then,
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```

```
sudo gedit /etc/modprobe.d/blacklist
```
then blacklist the bundled driver by adding the line at the bottom of the list:
blacklist bcm43xx

```
sudo gedit /etc/network/interfaces
```

and add the following lines:
```
auto wlan0
iface wlan0 inet dhcp
```

That should get your wireless working. If not or if you get any error messages, give me another shout.

---

