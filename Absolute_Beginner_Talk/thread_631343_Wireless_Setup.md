---
title: "Wireless Setup"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by dingclancy on 2007-12-04
So does ubuntu detect a wireless network from a fresh install? Or do I have to config it. 

My office has no wireless internet for three days but now I am starting to wonder if it is just my laptop.

---

### Post by pedro_orange on 2007-12-04
If your wireless card has it's drivers installed correctly then Ubuntu should detect the wireless network automatically. 

I was one of the lucky ones (I researched what kind of PCI-Wireless Cards worked well on Ubuntu & invested in that) - so when I booted up from LiveCD my NIC just worked. 'Ave it

It may be an idea to check the WLAN is up in an environment more familiar to you. If it works there it might be a config problem. Google your wireless card type/manufacturer to see if you can find other people who have come accross similar problems & how they solved them.

---

### Post by OffAxis on 2007-12-04
depends on the wireless card and how well it's supported.

```
iwconfig
```
will tell you if a wireless card is detected on your system.

```
iwlist [wlan0] scan
```
will tell you what networks have been detected.

wlan0 = the name of your network card

how to connect?
depending on your setup you'll need to supply a WEP or WPA key, or none at all.
see the man page of iwconfig for more info.
```
man ifconfig
```

you can also edit the interfaces file directly if it hasn't been setup
```
sudo nano /etc/network/interfaces
```

Here's a link to the community docs on the subject:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by dingclancy on 2007-12-04
Thanks!! I got this:

israel@israel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

israel@israel-laptop:~$ 



Seems like they  Ubuntu found the wireless card.... 
What is next?

---

### Post by OffAxis on 2007-12-04
next is finding the wireless network (the router) to connect to.

```
iwlist eth1 scan
```

will tell you what wireless routers are available to the card.

after you find that out, you can set the essid (the wireless network name) with
```

sudo iwconfig eth1 essid "name of router here"
```

```
ifup eth1
```

```
ifdown eth1

```
will bring the connection up/down if need be.

To run or re-run the dhcp ip request you can use
```
dhclient eth1
```

do you have security on this router?

---

### Post by jackpetrilli on 2007-12-04
> **dingclancy said:**
> So does ubuntu detect a wireless network from a fresh install? Or do I have to config it. 

My office has no wireless internet for three days but now I am starting to wonder if it is just my laptop.

As it is, Ubuntu defaults to 10 Mbps on a Wireless.  There's an add-on (whose name escapes me -nwdis?), that'll jump you up to 50 Mbps.  Do a google search on Ubuntu wireless.  You'll find it as I did.  There's 4 or 5 terminal commands that'll get you up and going.

- Jack

---

### Post by OffAxis on 2007-12-04
```
sudo ethtool eth1
```
should give you stats on your device (I know it works on a wired connection, never tried it on a wireless).

---

### Post by dingclancy on 2007-12-06
> **OffAxis said:**
> next is finding the wireless network (the router) to connect to.

```
iwlist eth1 scan
```

will tell you what wireless routers are available to the card.

after you find that out, you can set the essid (the wireless network name) with
```

sudo iwconfig eth1 essid "name of router here"
```

```
ifup eth1
```

```
ifdown eth1

```
will bring the connection up/down if need be.

To run or re-run the dhcp ip request you can use
```
dhclient eth1
```



do you have security on this router?

No there is no security in this router.

I got this --> 

```
Settings for eth1:
        Link detected: no
israel@israel-laptop:~$ iwlist eth1 scan
eth1      No scan results
```

It looks it can't scan for a wireless network but the internet cafe said the router is on.

---

