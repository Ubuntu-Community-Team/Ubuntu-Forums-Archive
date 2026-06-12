---
title: "Wireless Issue"
date: 2007-07-10
forum: BSD
---

### Post by helliewm on 2007-07-10
I have installed Desktop BSD. My wireless card is flashing as it seems to be recognized. It does this in Ubuntu so its all looking promising but I cannot find anywhere to connect to the internet to input my WEP key?

I am not use to KDE as I have previously used gnome so I am probably missing something?

Where do make my wireless connection and input my WEP key?

Helen

---

### Post by nphx on 2007-07-10
```
sudo ifconfig wlan0 up
```

```
iwconfig wlan0 essid your-wireless-net-work-name-here
```

```
sudo iwconfig wlan0 your-WEP-key-here
```

```
sudo dhclient wlan0
```

**NOTE:**  wlan0 might not be assigned to your wireless device i can be wlan1 also. To list your network devices:

```
ifconfig
```

For information:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by helliewm on 2007-07-10
Thanks ever so much. I have wireless problems with Feisty due to a documented bug so thought I would give Desktop BSD a go. Will try this, thanks again.

Helen

---

### Post by theonlyrealperson on 2007-07-11
I think DBSD has that fancy gui app too, it should work with WEP keys (but not WPA, sadly).

If you still have problems after trying nphx's fix or the gui app, make sure your firmware for the wireless card is loaded. The driver may be already compiled, but the firmware may still need to be loaded.

---

### Post by helliewm on 2007-07-11
How do I install the firmware? Have used Ubuntu extensively but not BSD. 

I did some more research last night and am wondering if PCBSD is a better option it has a very active forum?

Helen

---

### Post by theonlyrealperson on 2007-07-12
It's really easy if it has a port. I don't know what kind of wireless card you have, but I have a Intel 2200BG. The firmware for that card in FreeBSD 6.2 (which is what the newest DBSD is based on) is iwi-firmware-kmod. So:

```
su root
cd /usr/ports/net/iwi-firmware-kmod
make install clean

```

and then you have to load the module at boot. usually all this is is adding a line or two to /boot/loader.conf and /etc/rc.conf.  It depends on your card, so you'll have to do some Google searching for what to add. (Unless you also have the 2200BG, then I can point you in the right direction.

If you want to look to see if your card has a port, I think the best place to search is [http://www.freshports.org]("http://www.freshports.org")

I use PC-BSD quite a bit, and I really like it. But, you'll have to do this same thing there too.

---

