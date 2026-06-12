---
title: "Problem getting wireless card to work"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by darrentownsend on 2007-11-07
I am new to Ubuntu (feisty) and having problems trying to get my wireless card to connect to my modem. I am using a Compaq Presario 2500 PC with a Belkin F5D7011 wireless card. Modem is a BT Voyager 2110 ADSL Wireless Modem. I can connect to the internet fine with an ethernet cable but just cant seem to get the wireless connection to work. I can see the wireless connection listed in system-admin-network and it seems to be configured ok. Can anyone please help ? Below I have listed the output from my 1) "iwconfig", 2) "ifconfig" and 3) "route" commands.
darren@darren-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"v"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:367A-3837-6335-3861-716E-3677-36   Security mode:open
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

darren@darren-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:5F:00:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699599 (683.2 KiB)  TX bytes:134437 (131.2 KiB)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:972 (972.0 b)  TX bytes:972 (972.0 b)

darren@darren-laptop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
darren@darren-laptop:~$ 

Thanking you in advance :confused:

---

### Post by Pumalite on 2007-11-07
I'm not very good at wireless, but I have a collection of links that you might find useful:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by darrentownsend on 2007-11-07
Thanks for that, I will look through those and see if I can work it out.

---

### Post by bonestonne on 2007-11-07
what kind of network are you connecting to, and have you tried just using plug 'n' play networking?

i haven't tried using a belkin adapter, but if you go System>Administration>Network do you see the adapter listed Wireless Internet?

what you then do is configure it as Roaming [so that it will autoconnect to the strongest open network or you can configure it to connect to whatever WEP'd network you want. works fine for me on both a Linksys WMP11v3 and a Netgear WG111v2. one is USB, one is PCMCIA.

i hope that helps...its hard to say sometimes with wireless internet because i don't like using ndiswrapper until i absolutely have to.

---

