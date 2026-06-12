---
title: "Wireless internet connection."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-04-16
Hey guys.

I am having problems connecting to a wireless internet connection. It seems to me my card is functioning properly, because this is what I see when using the wifi manager.

[IMG]http://img234.imageshack.us/img234/151/snapshot37et.jpg[/IMG]

However no IP is assigned, and I cant go to any web pages. Any Ideas. I am using Kubuntu Dapper, and don’t really know what I’m doing :p

---

### Post by Ensnared on 2006-04-16
Chances are you just need to configure your settings with the WEP-key for the wireless network. There are several ways to do this, and I personally prefer the "old" way ;)

Open the file /etc/network/interfaces with your favourite text-editor (you need root privileges to save any changes made).
Look for the line that starts with "iface eth1" or "iface wlan0" - the line that defines your wireless adapter (it defaults to eth1 if you also have a regular network adapter as far as I know - if you only have the wireless adapter it's probably eth0 instead).
Make sure the line looks like this:
```
iface eth1 inet dhcp
```
Then, just below that line, add the following:
```
wireless-essid NETGEAR
wireless-key your-wep-key
```
I see from your screenshot that the ESSID is "NETGEAR", but I've no idea what your WEP-key is, but simply add that, then shut the device off then on again like this:
```
sudo ifdown eth1
sudo ifup eth1
```
Same goes for the interface name - eth1, wlan0 or eth0.

Chances are it'll work then, provided the driver is actually working properly.

---

### Post by Paul Bennett on 2006-04-16
Thanks so much man. 

Here this though. There is no WEP key. (I did not set this network up, its my uncles)

i.e, in windows XP, my card finds it and connects automatically. No Key is entered.

Thanks again.

---

### Post by Papa-san on 2006-04-16
I had a heck of a time trying to get my wireless to work. Your card is different than mine, but some of the links in my signature may be of help...

---

### Post by jimrz on 2006-04-16
Try editing to just "wireless-essid NETGEAR" or, if you want to be able to be automajically connected to other open networks elsewhere, substitute "ANY" for "NETGEAR". Then, leaving out the part about "your WEP key" (since there is none), follow the rest of the instructions by Ensnared above. Might just work.

---

