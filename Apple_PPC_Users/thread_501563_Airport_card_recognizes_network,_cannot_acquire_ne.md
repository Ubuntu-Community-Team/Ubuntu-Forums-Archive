---
title: "Airport card recognizes network, cannot acquire network address"
date: 2007-07-15
forum: Apple PPC Users
---

### Post by 0graham0 on 2007-07-15
Hi all,

**The Problem**

When I select the wireless network I would like to connect to with an Airport Extreme card, I get "Requesting a network address from the wireless network" but I never connect. Any help will be greatly appreciated...

**Some Quick Background Notes on the Problem:**

I just installed Fiesty on a Powerbook G4.

The first step I took was following the instructions for extracting the firmware with fwcutter at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

This led to a slight improvement... No wireless networks were detected before, but now I can detect my normal wireless network "default" in the gnome menubar, and if I run

```
sudo iwlist eth1 scan
```

Terminal Responds:

eth1      Scan completed :
          Cell 01 - Address: 00:0F:3D:46:85:5D
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=87/100  Signal level=-62 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 384ms ago

---

### Post by gordonh on 2007-07-15
sudo dhclient eth1

seems to work for me.  Network manager doesn't know that though, it still say "no network connection"

---

### Post by 0graham0 on 2007-07-15
Here's the results from sudo dhclient eth1:

# sudo dhclient eth1

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:03:93:ed:2d:7d
Sending on   LPF/eth1/00:03:93:ed:2d:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

...hmmm, do i add anything to that code?

---

### Post by uberlinux on 2007-07-16
It looks like it's doing it's job sending out beacons, just isn't hearing anything in return.  Are you maintianing a hardare access list on the router? (MAC filtering)  I know this is probably obvious, but now we can get that out of the way.

---

### Post by 0graham0 on 2007-07-16
Nope, there's actually no security at all (WEP, MAC Filter, etc.) It connects fine when I boot into OS X, just can't connect in Linux...

---

### Post by 0graham0 on 2007-07-16
Also...

If I go into Network Manager, and stop the wireless card from roaming, then type in the name of the network I want to connect to, the wirelesss will show up as connected (93% signal) but i cannot access web pages or the router...

---

### Post by tcrroadie on 2007-07-17
If the WAP that you want to connect to is ESSID:"default", then edit you /etc/network/interfaces file as follows. 

First, In a terminal run 
```
sudo ifdown eth1
```

Now lets edit your network settings file.
```
sudo gedit /etc/network/interfaces
```

Edit the bottom of this file for eth1 to look like this.  

```
auto eth1 
iface eth1 inet dhcp
wireless-essid default
wireless-key open
```

Save this file and exit gedit. 

Now restart eth1 

```
sudo ifup eth1
```

Please post the output you receive from sudo ifup eth1

Then post the output from ifconfig and iwconfig. 

```
ifconfig
``` 

```
iwconfig
```

If you are still having problems receiving a network address, try changing the wireless-key setting in your /etc/network/interfaces file to off. 

```
auto eth1 
iface eth1 inet dhcp
wireless-essid default
wireless-key off
```

Then run 

```
sudo ifup eth1
``` 

Please post back with your results.

---

### Post by neatokino on 2007-07-17
Hello-

I've got a similar problem connecting my 12" powerbook (1st generation) to my new Airport Extreme base station (I posted the problem in another thread on this forum, too).  

I've gone through all these steps here, and I finally was able to get bars and, in theory, a connection to the Airport Extreme, but I don't actually get an internet connection.  

The base station and airport card work just fine together when I boot up the powerbook in OSX, so I know it's not a hardware issue.  I was able to connect to an apple airport express router in Ubuntu yesterday.   I also can connect fine with an ethernet cable.

Do I need to setup my base station differently?  As I said, it works fine with the other macs in my household and works fine with the 12" PB on OSX. 

This is hugely frustrating because it should be able to work.  Any thoughts?  Does anyone have this particular configuration actually working?

---

### Post by 0graham0 on 2007-07-17
In response to TSRRoadie's post:

After editing /etc/network/interfaces with

```
auto eth1 
iface eth1 inet dhcp
wireless-essid default
wireless-key open
```

The output read:

```
graham@Me:~$ sudo ifup eth1 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth1/00:03:93:ed:2d:7d 
Sending on   LPF/eth1/00:03:93:ed:2d:7d 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 
```

```
graham@Me:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0A:95:9C:B1:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:41 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:03:93:ED:2D:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:211 errors:0 dropped:50 overruns:0 frame:0 
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:77440 (75.6 KiB)  TX bytes:11784 (11.5 KiB) 
          Interrupt:52 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:95:9C:B1:78  
          inet addr:169.254.8.37  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1588 (1.5 KiB)  TX bytes:1588 (1.5 KiB)
```

```
graham@Me:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306" 
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

After setting wireless-key to off in /etc/network/interfaces

```
graham@Me:~$ sudo ifup eth1 
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth1/00:03:93:ed:2d:7d 
Sending on   LPF/eth1/00:03:93:ed:2d:7d 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.
```

---

### Post by 0graham0 on 2007-07-19
-please delete-

---

### Post by tcrroadie on 2007-07-19
Are you dual booting with OS X?

When you installed bcm43xx-fwcutter did you use apt?

```
sudo apt-get install bcm43xx-fwcutter
```

Two things on my mind at the moment.  

1.  Incorrect firmware used for the wireless chipset (BCM4306) used in your PowerBook.

2.  Radio interference in the area you are trying to connect to a wireless network.  Do you live in an apartment?  My iBook doesn't like the cordless telephone in my house.  When the phone is in use, wireless on Linux is dead on my iBook. 

I am thinking that your wireless card should be working properly since you are receiving information about your wireless network when you run "sudo iwlist eth1 scan"
```

eth1 Scan completed :
Cell 01 - Address: 00:0F:3D:46:85:5D
ESSID:"default"
Protocol:IEEE 802.11bg
Mode:Master
Channel:1
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=87/100 Signal level=-62 dBm Noise level=-71 dBm
Extra: Last beacon: 384ms ago
```

You may want to try setting up your network with static addressing, to see if that may get you a connection.  You can use Gnome Network Manager to set your network settings.  Though I am thinking that since you are not receiving an address using DHCP, that using static addressing may not work either.  

Can you try connecting to another wireless network?  School, coffee shop, friends house.

Well, time for me to get some zzzzzzzzzzzzz's

---

### Post by neatokino on 2007-07-21
I've tried just about everything and still haven't been able to get my 12" powerbook to connect wirelessly to my very-recent-model Airport Extreme base station (the one that runs wireless-n).  

I have been able to get bars, so my airport card is definitely communicating with the base station, but I just can't get on the internet.  

After going through every post I could find here and trying every suggestion I could understand (couldn't quite get through the french posts about updating firmware), I was  ready to give up on Linux altogether for now.  It was especially frustrating because when I boot up on OSX, the wireless works perfectly.

I did, however, happen to have an older model Belkin wireless-g router, and I set it up in place of the Airport Extreme base station.  With 64bit WEP it works absolutely fine for me running Feisty.  

So I guess the problem has to do with settings on the Airport Extreme base station.  I ran through many different settings with no success.

I'd much prefer to use the Airport Extreme base station rather than the Belkin.  Is there anyone here who's had success connecting a powerbook with the newest model Airport Extreme Base Station?

TIA
Michael

---

