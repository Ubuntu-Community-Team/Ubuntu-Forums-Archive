---
title: "GAH, how do I activate wlan0???"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2007-05-30
I just tried to install the drivers for my Broadcom 1390 wireless network card.

This was after a fresh install of Feisty (I formatted the hard drive).  When I go to System->Administration->Network, wlan0 does not show up.

How do I get that card to show up?

---

### Post by ncappel1 on 2007-05-30
try doing
```
ifconfig -a
```

If you can see that your device is there, but the flag is down, that is, not "UP"
```
ifconfig [device name] up
```

if that works, then the next step is to have it start doing what it does, try to have it find the essid with
```
iwconfig [device] essid any
```
then 
```
 iwconfig [device] ap any
```

the ap is the access point, you are telling the computer to connect to any essid and then any accesspoint. The man pages are really helpful with this, as is [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Was this helpful?

---

### Post by Mardok45 on 2007-06-06
ifconfig -a   did not show wlan0.

What now?

---

### Post by Outrunner on 2007-06-06
As far as I know, wlan0 would be the router(I think so at least). Your wireless adapter is usually called ath0 or eth1 in special cases(again , I THINK)

---

### Post by wreti on 2007-06-06
By "Broadcom 1390" do you mean Dell wireless 1390 wlan mini pci card?

---

### Post by Mardok45 on 2007-06-07
> **wreti said:**
> By "Broadcom 1390" do you mean Dell wireless 1390 wlan mini pci card?

Mini PCI

---

### Post by wreti on 2007-06-07
I got my 1390 mini pci card to work using ndiswrapper and this guide:
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html). It's fairly straightforward though you may have download a different driver than the one mentioned if you don't have a Dell 1501. Hope this helps.

---

