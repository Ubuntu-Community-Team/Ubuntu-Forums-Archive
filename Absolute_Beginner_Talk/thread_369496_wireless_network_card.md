---
title: "wireless network card"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Ircha on 2007-02-24
Ok, I'm trying to get internet to work, I managed to get it to work before, but when i restarted my computer suddenly it didn't work anymore, I used WiFi Radar to connect and suddenly I had my internet working, but when i restarted my computer internet was gone, and when trying to use Wifi Radar for it, it just fails. also I noticed my network card's lamp isn't glowing any more, but the linux ubuntu computer knows it's there, when i remove the wireless network card and type ndiswrapper -l it shows 
]driver[         driver installed
and when i put in the network card again, and type sudo ndiswrapper -l it says
]driver[         driver installed, hardware present.
so I tried typing iwconfig, and when I do that, it says..
lo no wireless extension
eth0 no wireless..
sit0 no wireless..
wlan0 IEEE 802.11g ESSID:off/any
         mode:Managed Frequency2.407 GHz Access Point: Not-associated
bit rate:54Mb/s Tx-Power:-2147483648 dBm sensitivity=0/3
rts thr:65535 B Fragment thr:65535 B
Power management: OFF
Link quality:0 Signal level:0 Noise level:0

How do I fix this? When I can get this to work i'll install wireless network assistant to keep track of things.

EDIT:
Also, when I press System/administration/networking there is a wireless connection option, it's essid: Thornet and adress: DHCP, with a network password in hexadecimal, and also there are two other options, modem, and wired connection.

---

### Post by wetland on 2007-02-24
What type of card ?

I have an Atheros card and use the command line to start it.

```
sudo ifconfig ath0 up 
```(ath0 is my card).

```
sudo iwconfig ath0 essid ( your access point)  key ( your wep key)

``` Dont use the parenthesis.
```
sudo dhclient ath0
```

---

