---
title: "wireless networking: bars but no signal"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2007-07-15
can anyone please help??!!

[http://ubuntuforums.org/showthread.php?p=3023669#post3023669](http://ubuntuforums.org/showthread.php?p=3023669#post3023669)

---

### Post by theDaveTheRave on 2007-07-16
PompeJohn.

Not really very much information for us here,  and probably explains the lack of responses so far!

So here are a few things that will give us some idea of what your problems are.

You say that you have "bars" on the network connection icon, which is always a good sign!

First place to start, what wireless card are you using - do you know??

From the command line run

> 
davemyers@Aramis:~$ sudo lshw
Password:
aramis       
*-network
                description: Wireless interface
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 3
                bus info: pci@0a:03.0
                logical name: wifi0
                version: 01
                serial: 00:19:7d:40:b8:c0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=192.168.2.3 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:d0000000-d000ffff irq:18


- I have edited the resulting output a little, as you'll find out!

You do need to run this as SUDO or you don't get all the details of the hardware that are available.

As you can see from my output I am using an atheros wireless chip.

Once you have done this do a 

> 

davemyers@Aramis:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:17:3F:15:5D:43
                    ESSID:"Mousquetaires"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/94  Signal level=-43 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:14:6C:FE:E6:2E
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra:ath_ie=dd0900037f0101001dff7f

eth0      Interface doesn't support scanning.



Here you can see that the eth0 interface  supports the scanning  for any wireless routers. In this case it is hooked in to my system <mousqeutaires>, I am also picking up another system that doesn't have a name!

wifi0 interface is the software that "wraps" up the controller to make the atheros chip work, essentially you can think of it as a bit of software that converts the regular windows functions into something that a linux kernel can understad (a little bit like wine, just for a wireless card).

If you can run these 2 commands and post the details of the results into your post you should get more help.

Also once you have the details of the chip (again in my case an atheros AR5005g... blah blah blah..) you can run a search for the item in google, to see what it turns up.

good luck and post back again soon.

Dave

---

### Post by dkfinger on 2008-01-13
I have over 50% signal showing on the wireless network I am attempting to connect to. However, when I connect, it shows that the signal strength is 0%, and only a physical address shows in connection properties.  The IP address does not show up.  I have done the things that theDavetheRave suggested, and here are my results concerning the network card.

           *-network:1
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:23:8e:36
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

I had heard that this specific card has had problems with 7.10 (the version I am using), however, the bcm43xx driver I obtained installed perfectly.

eth1      Scan completed :
          Cell 01 - Address: 00:40:96:38:37:F3
                    ESSID:"NNU-Open"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=74/100  Signal level=-64 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 88ms ago

As you can see, I am attempting to log in to an unencrypted network that the card picked up seemingly without a problem.  I just don't understand why it doesn't have any signal strength.  What can I do to fix this?

---

