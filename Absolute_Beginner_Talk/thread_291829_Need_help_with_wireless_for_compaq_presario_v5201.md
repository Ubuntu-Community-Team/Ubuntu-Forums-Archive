---
title: "Need help with wireless for compaq presario v5201"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by jonnylost on 2006-11-03
Hi there, this is my first post, and I just started using Linux a few days ago.  I am not familiar with commands at all just to let you know in advance.

Ok, so I reformatted my HD and installed ubuntu 6.1, and now I can not get my wireless to connect on my Compaq Presario V5201US Notebook PC.  I downloaded ndiswrapper, but have no idea what to do with it.  Any help would be great

---

### Post by DSn0wMan on 2006-11-03
You might start by letting us know what type of wireless card you have, as different methods are needed for different cards.

If you are not sure what you have, you can find out by opening a terminal (Applications -> Accessories -> Terminal) and typing ```
lspci | grep -i network
```

---

### Post by chriscando on 2006-11-03
First off, you will need the .inf file for you cards driver. Easiest way to get this is if you dual boot with windows and have your wireless working there.

Once you have that you can install it with
```
sudo ndiswrapper -i driver.inf
```
where driver.inf is the driver.inf from windows

then you can issue
```
ndiswrapper -l
```
to see if it installed your driver correctly.

if so, you can activate it by
```
sudo modprobe ndiswrapper
```

If this all goes well, you can see if your card is up by
```
ifconfig
```
hopefully you will see wlan0 or something like that.

Thats the general sequence, post any problems you have.

---

### Post by jonnylost on 2006-11-03
> **DSn0wMan said:**
> You might start by letting us know what type of wireless card you have, as different methods are needed for different cards.

If you are not sure what you have, you can find out by opening a terminal (Applications -> Accessories -> Terminal) and typing ```
lspci | grep -i network
```


Thanks,
Network Controller: Broadcom Corporation BCM4318 (Airforce One 54 g) 802.11g Wireless LAN Controller

Sorry, I don't have Windows installed on my laptop right now, I am trying to stay away from it.

---

### Post by Compcort on 2006-12-07
I was running Ubuntu, until I gave up trying to connect with wireless. My laptop adapter is by Broadcom, 802.11b/g WLAN version 4.10.40.0 at the location: PCI Slot 3 (PCI bus 6, device 2, function 0).
I tried installing the ndis wrapper, but don't understand Linux instructions/terminology.
I also looked at [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)
Thank you for looking at this with me.

---

