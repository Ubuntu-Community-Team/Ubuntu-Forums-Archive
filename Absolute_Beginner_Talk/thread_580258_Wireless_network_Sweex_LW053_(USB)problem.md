---
title: "Wireless network Sweex LW053 (USB)problem"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Kevf on 2007-10-18
I've read numerous pages and can't seem to get it working. 

Things I've done:

entered Essid: exactly the samen as on this laptop
entered my wep key: exactly the same
entered the dns server

I allready looked on my windowsdriverinstallcd and it says rt2500, but according to this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

It should work out of the box with 7.10 (Just got it today :))

lsusb:

Bus 003 Device 002: ID 148f:2573 Ralink Technology, Corp

The light on the dongle does work, so I assume it's recognized. 

Hope someone can help me on the right track :popcorn:

---

### Post by Kevf on 2007-10-19
I'm one little step further....I think I have to use this file (ralink actually has linux support)

[http://www.ralinktech.com.tw/data/RT25USB-SRC-V2.0.8.0.tar.gz](http://www.ralinktech.com.tw/data/RT25USB-SRC-V2.0.8.0.tar.gz)

But the readme file is hocus pocus for me. Just a little bit much for a beginner.....

and I've read something about blacklisting a different one? :confused:

---

### Post by Kevf on 2007-10-19
iwconfig:

```
 
lo    no wireless extensions

eth0 no wireless extensions

wmaster0 no wireless extensions

wlan 0 IEE 802.11g  ESSID: "DV201AM"
Mode: Managed     Frequency: 2.462 GHZ   Access Point 00:1A:92:5B:44:E8
Retry min limit:7 RTS thr: off   Fragment thr= 2346 B
link signal level = -54dbm
Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0  Missed Beacon: O
```
sudo cat /etc/network/interfaces

```
iface wlan0 inet static   (note: heb dynamic ook al geprobeerd)
adress 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1
wireless key  (niet handig om die te plaatsen toch? heb iig een tien cijferige)
wireless - essid DV201AM

auto wlan0
```
 Maybe this helps?

had to type in on my xp laptop ;)

lsmod gives rt2500 and rt73usb. Should I blacklist rt73usb? and what's the exact code for it? (sudo nano /etc/modprobe.d/blacklist?)

---

### Post by Kevf on 2007-10-19
Ok something really strange happened. I've blacklisted the rt module I've mentioned before and still no internet. It dit fix another problem: gutsy is fast again. One of the other problems was the speed of the os. It was 10 times slower than xp........ didn't have that problem with feisty.

After I blacklisted rt73usb everything speeded up to very fast!!! Maybe something to look into for the experts? 

Still no internet though :(

---

### Post by Kevf on 2007-10-19
Clues someone? Have a day off so this is my only 'gutsy-day' this week :popcorn:

---

### Post by Kevf on 2007-10-20
Can anyone tell me if there's something wrong with my question? Or am I to impatient (I know that can be quite irriritating at a forum). 

But using the internet is one of the things that just have to work and I would hate it to have to deinstall Ubuntu again :(

---

