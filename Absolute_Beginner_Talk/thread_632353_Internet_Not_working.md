---
title: "Internet Not working"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by keeZey on 2007-12-05
It finds my wireless card and the my home wireless connection and connects to it, but thats all it does :s
Anyway around it?
Not sure what make it is but i think its an intel one

---

### Post by JustinAlf on 2007-12-05
1) What distro are you using
2) What kind of wireless?   USB, Internal?
3) Are there any passwords to your connection?  WPA,WPA2,WEP?
4) What brand is your wireless card?  If you know this, what is your chipset?  Ralink, rt61?

This info could help

---

### Post by keeZey on 2007-12-05
ubuntu lastest
internal wireless (laptop)
there is no password to connection 
just found out its a ralink RT73 card

---

### Post by philinux on 2007-12-05
Can you plug your lappy into router directly just to make sure you can get internet from there.

---

### Post by OffAxis on 2007-12-05
can you ping your router?

```
sudo -c 4 ping [router ip]
```

also, some community docs on the subject:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by keeZey on 2007-12-05
it has vista on it also which runs net fine..
i just tried to load a page again it seems to load part of it but doesnt display anything on the actually page.. just shows the title and that it transfered same data. Tried to ping aswell but that doesnt work. its really werid

---

### Post by WebSiteGuru on 2007-12-05
I , also, am having the same problem with one of the computer I tried to set up for my uncle.  It accepted the connection but no traffic coming through at all.

---

### Post by keeZey on 2007-12-05
i tired that link you gave me OffAxis but again doesnt work
it doesnt say that the page cant be loaded just gives me a blank white screen

---

### Post by OffAxis on 2007-12-05
what kind of router do you have?

can you ping the loopback?

```
sudo ping -c 4 localhost
```

does your card go up / down when the connection drops? or does it stay 'connected'?

---

### Post by keeZey on 2007-12-05
it does loopback when i do at code
it isnt a high router kind of old but all my other pcs connect and use it fine

---

### Post by OffAxis on 2007-12-05
can you ping any other machines on the network?

your mode might be set up as 'Ad-Hoc' or something...
could you post the contents of a 

```
sudo ifconfig
```

---

### Post by keeZey on 2007-12-05
cant ping any other machines 

eth0      Link encap:Ethernet  HWaddr 00:03:0D:6D:B7:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:A0:80:06  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fea0:8006/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155667 (152.0 KB)  TX bytes:57268 (55.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-10-60-A0-80-06-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by OffAxis on 2007-12-05
sorry that shoulda been an iwconfig

```
sudo iwconfig
```

---

### Post by keeZey on 2007-12-05
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:38:29:C5   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by keeZey on 2007-12-05
any ideas?

---

### Post by OffAxis on 2007-12-05
how about 

```
sudo iwlist wlan0 scan
```

your laptop's ip address, did you manually specify that or did it get it from the dhcp server?

Can you see the laptop consistently from the router?
There should be page on the router for 'Attached Devices' or 'Wireless Connections' or something like that.

---

### Post by keeZey on 2007-12-05
that was giving to me as i connect to the router
yeah i can see the laptop constantly from the router apart it doesnt show the name just the ip of it

wlan0           Scan completed  :
                    Cell 01 - Address: 00:0F:3D:3829:C5
                                  ESSID:"default"
                                  Mode:Master
                                  Channel:6
                                  Frequency:2.437 GHz
                                  Signal level =-58dBm
                                  Encryption key:off
                                  Bit Rates:1 Mb/s; 2Mb/s; 5.5Mb/s; 11Mb/s; 22Mb/s
                                  Extra:tsf=000000000f684489

---

### Post by OffAxis on 2007-12-05
Weird. It looks like it's connected properly.
You can try power cycling the router or upgrading the firmware (longshot).

How does your route table look?
```
route
```


you can also request another ip from the dhcp server and see if it can negotiate one.

```
sudo dhclient
```

by the way, I don't know if you named your router "default", but that may not be the best name; in my mind it falls into the same class of reserved words that things like 'time', 'date', or 'localhost'- it PROBABLY won't be an issue, but there's a lot of room for error under the umbrella of 'Probably'.

---

### Post by JustinAlf on 2007-12-05
Try Wicd, I know some users of the Ralink chipsets say it works bettor.
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by keeZey on 2007-12-05
the route table looks fine to me and that code you gave doesnt work?
Havnt tried Wicd but will now
Wont let me install wicd as it conflicts with network manager?

---

### Post by keeZey on 2007-12-05
Installed Wicd and its still the same :(

---

### Post by JustinAlf on 2007-12-10
I had this similar problem.  It went away when I would connect manually with Network-manager or WICD, but only if I had a password.  I'm not sure why that is, but try to put a password on your router and see if you can connect manually when you have a password.  I"m not sure why this seemed to work for me, but it did.

---

