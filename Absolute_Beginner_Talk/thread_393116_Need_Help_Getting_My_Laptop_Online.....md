---
title: "Need Help Getting My Laptop Online...."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2007-03-25
I just installed Ubuntu Edgy Edt 6.10 on my Dell 600m laptop. I got everything installed fine, added some pakets from the CD, but I can't get it online. It has wireless, but at this point I think it would be easier to go wired. That's all the info I can think of unless you guys ask me some questions. I am using a Belkin wireles router, also.

---

### Post by teaker1s on 2007-03-25
plug in ethernet cable and if you don't get automatic connection setup

Try router address-if this works but no www. you need either static ip and isp DNS set up in
top desktop panel
 system>administration>networking
or dhcp and this link
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

---

### Post by Minker17 on 2007-03-25
I can't get into my router and there are no lights on the port in the back of the laptop. Someting did just occur to me though. This i a brand new hard drive, replaced by Dell, that had no OS on it in the first place.

Is it possible I need a driver for it?

---

### Post by Bachstelze on 2007-03-25
Nou, you shouldn't need to install one as the driver should already ship with Ubuntu. Open a terminal and run *sudo ifconfig -a*. What do you get ?

---

### Post by scrooge_74 on 2007-03-25
need specs for the ethernet wireless, and possible you just need to sudo dhclient eth0 (eth0) is probably your wired card.

with the ifconfig you can tell us if the systems detects the wireless card.

is important to know the brand and possible the model of the wireless card.  Also for initial testing disable security on the wireless router

---

### Post by Minker17 on 2007-03-25
etho 0
link encap:ethernet hwaddr 00:0e:35:8e:f2:68
inet addr:192.168.2.1 bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::20e:35ff:fe8e:f268/64 Scope: link
Up broadcast running multicast MTU:1500 Metric:1
RX packets:8203 errors:0 dropeed:0 overruns:0 frame:0
Tx packets: 972 all the rest except carrier are 0. carrier: 1
collisions:0 txqueuelen: 1000
rx bytes:0 )0.0b) TX bytes:0 (0.0b)
Interrupt: 5 Base address: 0x4000 Memory: fafff000-faffffff

Then lo and some stuff and sit0 and stuff. Do you need that as well?

---

### Post by Bachstelze on 2007-03-25
Try :

```
sudo dhclient eth0
```

---

### Post by scrooge_74 on 2007-03-25
yes it seems your system recognizes the wireless as sit0, still we need to know the brand of the wireless card.

From what I can see you are online with the wired card.

There are different how tos for different wireless cards.  I have three laptops and one got wireless out of the box, another one had do some tweaking and the third one uses a broadcom card and I had to follow and specific Howto

---

### Post by Minker17 on 2007-03-25
> **HymnToLife said:**
> Try :

```
sudo dhclient eth0
```

What exactly am I looking fr when I run that?

Also, I will find out what the wireless card is.

---

### Post by Minker17 on 2007-03-25
I checked it on Dell.com and this is what the laptop apparently has:

CARD (CIRCUIT), WIRELESS, CAPACITOR, INTEL2100
MODEM, 56K, INTERNAL, MODEM DAUGHTER CARD, BROADCOM POLARIS MODEM

---

### Post by Bachstelze on 2007-03-25
It will tell your wireless infrface to try and connect to any DHCP servenir it can find. If you see something like this :

```
bound to 10.1.204.62 -- renewal in 27793 seconds.
```

That means your inferface found your router. You should now be able to go online.

---

### Post by Minker17 on 2007-03-25
It listened and sent. 
No DHCPOFFERS recieved
No working leases in persistent database - sleeping -

---

### Post by Minker17 on 2007-03-25
eth0 is sending and recieving, but I stil can't get on. If that helps at all.

---

### Post by Minker17 on 2007-03-25
Bump?

---

### Post by scrooge_74 on 2007-03-25
> **Minker17 said:**
> I checked it on Dell.com and this is what the laptop apparently has:

CARD (CIRCUIT), WIRELESS, CAPACITOR, INTEL2100
MODEM, 56K, INTERNAL, MODEM DAUGHTER CARD, BROADCOM POLARIS MODEM

This is of no help, is this machine a dual boot? If so copy the info from the PC properties in windows.  Or check with DELL, you really need to know which wireless card you have.

> **Minker17 said:**
> eth0 is sending and recieving, but I stil can't get on. If that helps at all.

if you say the wired card is sending and receiving then check to see if you can ping a website like yahoo.com, do a ping [www.yahoo.com](www.yahoo.com)

also possibly your computer does not know which DNS server to use, you can add then in the system>network>DNS servers, add Open DNS servers IPs

208.67.220.220, 208.67.222.222

---

### Post by Minker17 on 2007-03-25
Intel Prowireless 2200bg

It's receiving about 6x as many packets as it's sending.

I can ping my router, but not yahoo of google.

---

### Post by Minker17 on 2007-03-25
Now when I click on the ethernet box at the top it says I'm disconnected.

---

### Post by Minker17 on 2007-03-25
Great. Now whenever I go into networking, I get a bug buddy report and it crashes out.

Man, what am I doing wrong?

---

### Post by scrooge_74 on 2007-03-25
Did you tried this link?  [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

