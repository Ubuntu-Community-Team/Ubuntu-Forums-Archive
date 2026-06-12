---
title: "Wireless Driver Install-How?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by tomsr on 2008-02-24
I really could use some help installing the _correct _driver for my Linksys wireless USB adapter WUSB54Gv4 on Ubuntu 7.10. 

I have read other threads relating to this but none completely apply to my scenerio. I messed up my first install trying to get this darn thing to work and just completed a complete reinstall of Ubuntu-with updates. 

I did a network search- sudo iwlist wlan0 scan- and my device is recognized but no driver is listed.

I successfully pinged the router and an external address-google. Network manager shows I have good signal strength and even lists other networks in my neighborhood. However, when I type in my WEP key, I can't connect. I believe I need a driver installed.

I am a fresh-raw-newbie but I am trying. I would appreciate any help.
Thanks,
Tom

---

### Post by richaoj on 2008-02-24
did you make sure you have the right wep - is it ASCII or HEX etc.

---

### Post by toa on 2008-02-24
> **richaoj said:**
> did you make sure you have the right wep - is it ASCII or HEX etc.

Or the ip enabled to firewall (if used) or mac enabled to firewall (if used) or the WEP is right (TKIP or whatever.)

HAving recieving wireless networks and showing strength and other networks shows the wireless is working, make srue about the wireless router settings or anything your using .

---

### Post by tomsr on 2008-02-24
Thanks for your replys.
I have a Netgear cable wireless modem/router that I use with three other PCs-one a wireless Dell laptop and all run Vista. They all connect to the router without probem. I am not sure if my WEP key in ASCII or HEX but I have tried using bother without success on my Ubuntu computer.
As for the ip and mac settings, are you refering to these settings on Ubuntu or the router? I don't believe that they are my problem. I think it is a driver problem.

Thanks much,
Tom

---

### Post by tomsr on 2008-02-25
I am still working on this Linksys USB adapter. I really appreciate all the advice you are offering.

Below is a bunch of info I gathered on my Linksys WUSB54G on Ubuntu 7.10 (Still no connectivity.

sudo iwlist wlan0 scan

[sudo] password for tomsr:

wlan0     Scan completed :

          Cell 01 - Address: 00:18:F3:71:26:7C

                    ESSID:"stephens"

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz

                    Signal level=-33 dBm  

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=00000002f6f64170



wlan0     IEEE 802.11g  ESSID:""  

          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Encryption key:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlan0     Link encap:Ethernet  HWaddr 00:14:BF:7A:A8:B4  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:26898 (26.2 KB)


Hope this helps someone in the know to determine my problem.

Thanks much,
Tom

---

### Post by tomsr on 2008-02-29
Thanks everyone I have my wireless adapter up and running thanks to everyone's help.

Tahnks again,
Tom

---

