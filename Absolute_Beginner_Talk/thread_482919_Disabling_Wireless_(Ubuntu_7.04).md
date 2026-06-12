---
title: "Disabling Wireless (Ubuntu 7.04)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Trollax on 2007-06-24
So I'm running Feisty on a laptop (Compaq nx6120) and because I don't trust wireless one whit, I'd like to disable my wireless card a-la windows, so it's effectively off. ATM it's on the default "roaming mode enabled" I'd just like it to be whatever the Ubuntu equivalent of "off"

---

### Post by atria on 2007-06-24
Just ignore it and not connect to any networks?

I'm not sure how to do it with the GUI but it is possible to disable it through the console
```
ifconfig ethx down
```

where ethx is your wireless network device. It can be eth1, wlan0 etc.

---

### Post by Trollax on 2007-06-24
Didn't work.

---

### Post by wooglin280 on 2007-06-24
Try ath0 or wlan0.  Usually your wireless card is not ethx.  If you still cannot get this to work please post the output of ifconfig and iwconfig.

---

### Post by mattg89 on 2007-06-24
if you look at the output of ifconfig, one of the labels on the left will have Wireless as one of the options on the right. call that <ethx>

then do

sudo ifconfig <ethx> down

If it's usb is probably eth1
If it's pcmcia its probably wlan0

---

### Post by atria on 2007-06-24
And i hope you do realize that we're helping you out with our limited free time. Try to be more polite next time.

Well in any case, add a sudo infront of the command. You need root privileges to bring down a network interface.

---

### Post by Trollax on 2007-06-24
Nope the wireless is listed as eth1.

> **atria said:**
> And i hope you do realize that we're helping you out with our limited free time. Try to be more polite next time.

Well in any case, add a sudo infront of the command. You need root privileges to bring down a network interface.

My apologies, I was not intending to appear short, and I'm aware that this is done by people in their spare time.
Yes I used sudo at the front of it. The wireless device is internal, I dunno if that has something to do with it at all. if it was a problem with a plug-n-play device I'd just pull it out, but alas...

---

### Post by mattg89 on 2007-06-24
What would really help us if you could post the output of:

sudo ifconfig

and 

sudo iwconfig

---

### Post by nphx on 2007-06-24
```
iwconfig
```

-This will tell you what your wireless device is either wlan0 or wlan1

To disable it:

```
sudo ifconfig wlan0 down
```

Then to have it disabled on boot edit: **/etc/network/interfaces**

```
gksu gedit /etc/network/interface
```

And comment out 2 lines for your wireless device like this for example:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

[COLOR="Red"][B]#auto wlan1
#iface wlan1 inet dhcp[/COLOR]
[/B]

Save and exit. Now when you reboot your wireless device should stay down.

---

### Post by walkerk on 2007-06-24
remove it from your /etc/network/interfaces (when i did this my wireless stopped initiating..)

```
sudo gedit /etc/network/interfaces
```

remove:
```
auto wlan0
iface wlan0 inet dhcp
```

or whatever yoru wireless nic registers as (sometimes eth1).. also remove it from your iftab

```
sudo gedit /etc/iftab
```

remove the line corresponding to your wireless nic.. check the mac address. if you don't know it.. terminal:
```
ifconfig
```

save & exit.. reboot. :)

---

### Post by Trollax on 2007-06-24
okay. I think it's off. I can live with that for now anyways.

---

