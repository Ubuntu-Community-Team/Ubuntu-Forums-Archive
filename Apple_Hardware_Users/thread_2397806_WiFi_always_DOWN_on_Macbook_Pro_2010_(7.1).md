---
title: "WiFi always DOWN on Macbook Pro 2010 (7.1)"
date: 2018-08-03
forum: Apple Hardware Users
---

### Post by jnedbal2 on 2018-08-03
I'm having a really hard time getting WiFi work on my Macbook Pro 2010 (7.1) in Ubuntu.
It used to work for many years, then I messed up something and was never able to bring it back to life. I tried using a fresh installation on the internal HDD and the Live USB to no avail.

The card is:

```
:~$ lspci -nn |grep -i bcm
02:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```

On a fresh install, I'd get the firmware:

```
:~$ sudo apt-get install firmware-b43-installer
```

Make sure the modules are removed prior to inserting b43:

```
:~$ sudo modprobe -r b43 bcma
:~$ sudo modprobe -r brcmsmac bcma
:~$ sudo modprobe -r ssb
:~$ sudo modprobe b43
```

The WiFi is not blocked:

```
:~$ rfkill
ID TYPE      DEVICE      SOFT      HARD
 1 bluetooth hci0   unblocked unblocked
 2 wlan      phy0   unblocked unblocked

```

However the state of wlan0 is always DOWN:

```
[COLOR=#000000][FONT=Arial]:~$ ip a show wlan0
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether f8:1e:df:ed:bd:8a brd ff:ff:ff:ff:ff:ff
:~$ cat /sys/class/net/wlan0/operstate
down
[/FONT][/COLOR]
```

This won't change no matter what I try to do:

```
:~$ sudo nmcli radio wifi on
:~$ sudo ifconfig wlan0 up
```

I still get
```
[COLOR=#000000][FONT=Arial]:~$ ip a show wlan0
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether f8:1e:df:ed:bd:8a brd ff:ff:ff:ff:ff:ff
:~$ cat /sys/class/net/wlan0/operstate
down
[/FONT][/COLOR]
```

The WiFi card used to work for me in the past. It still works, when I boot to Mac OS X. I just don't seem to be able to get it from the DOWN state in Ubuntu. As far as I am aware, there is no hardware key on the Macbook Pro 2010, which could disable the card. Also, I tried Debian 9 on the computer instead of Ubuntu, to the same effect.

Anyone with ideas where to start? Could it be something to do with power management?

Thanks for any ideas and suggestions.

---

### Post by slickymaster on 2018-08-03
*Thread moved to **Apple Hardware Users**.*

---

