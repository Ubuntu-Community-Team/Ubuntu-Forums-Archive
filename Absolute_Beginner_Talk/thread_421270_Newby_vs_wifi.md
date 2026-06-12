---
title: "Newby vs wifi"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by k5ilf on 2007-04-24
:confused: I am the newest of newbys regarding Ubuntu. I have Feisty Fawn installed (by Wubi) but I don't know ANYTHING about installing drivers---the wifi card, Netgear MA311, is on the list as being supported, but don't know what to do next. Can anyone direct me to a 'step by step' guide for getting the card working?

Thanks,
bill in las cruces

---

### Post by AlexenderReez on 2007-04-24
actually you don't need to install anything to get wireless card to work....feisty comes with network manager. .. so it will detect it for you...but i really suggest to install wifi radar...for me...it is working better than network manager....if reffering graphic card...search howto in ubuntu forums....i 'm sure you will find a lot of guide about it...:KS

---

### Post by carloslosgrande on 2007-04-24
I've got a Netgear WGR614 and Feisty recognised it no trouble and setup the whole works except for the bit done by Netgear.
try this; -[HTML] http://www.routerlogin.net/start.htm[/HTML]
It worked well for me and I'm just a beginner.

---

### Post by Pobega on 2007-04-24
Can you run the following commands for me?

sudo ifconfig
sudo iwconfig
sudo iwlist eth2 scan

---

### Post by AlexenderReez on 2007-04-24
> **Pobega said:**
> Can you run the following commands for me?

sudo ifconfig
sudo iwconfig
sudo iwlist eth2 scan

about last command...better

> sudo iwlist scan

you have specific kind of scan...so it won't scan all kind of network available:)

---

### Post by sailor2001 on 2007-04-24
I like and have used for several years, the kwifi manager

---

### Post by k5ilf on 2007-04-24
Thanks for the information, but most of it was over my head. Here is what I have found out so far---I opened Ubuntu and right clicked on the double monitor on the right top. I have enable networking and enable wireless checked. Under connect info it shows wlan0 and under driver PRISM2_PCI   It has all zeros on the addresses.

It does not find any wireless networks when I left click.

The other programs listed or referred to are 'all Greek to me!' as it likely will take me another several months until I achieve the rank of newby!!

bill in las cruces

---

### Post by alibaba on 2007-04-24
have you tried wicd? I could'nt connect at all to anything, this is the only thing that helped me connect, 

[http://compwiz18.ig3.net/wicd/wb/](http://compwiz18.ig3.net/wicd/wb/)

hope this helps

---

### Post by k5ilf on 2007-04-25
Thanks for the info. I'll try and get it downloaded as soon as I figure out how to do it. Since I do not have access to the Internet in Fiesty, I will have to download it with windows and see where I can put it so Fiesty can find it---I used Wubu to install.

bill in las cruces

---

### Post by tuxcantfly on 2007-05-01
if you're using Wubi, just save it to C:\ on your windows drive, and when you boot feisty it'll be in /media/host

---

### Post by Pffester on 2007-06-16
Alright I'll take any help I can get with Ubuntu Fiesty:

I've got a Netgear wgr614 v4 wireless router and I don't know if its working or not. It works as a wired device. I'd like to set it up so I can use my wireless card Netgear WG121 on one of my other machines.

The wg 121 setup has been a TOTAL flop on any machine I've tried, BUT more on that later,
one machine at a time.

 On THIS machine , which would be the server (? next to the modem, wired connection) I get the following from the thread requests for information:

QUOTE:
sudo ifconfig
sudo iwconfig
sudo iwlist  scan

---------------------------------------------------------------------------------------------------------------
dan@dan-desktop:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:03:47:DC:AA:65
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fedc:aa65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:41842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44313277 (42.2 MiB)  TX bytes:8469169 (8.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6840 (6.6 KiB)  TX bytes:6840 (6.6 KiB)

dan@dan-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dan@dan-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

dan@dan-desktop:~$
---------------------------------------------------------------------------------------------------------------------

QUOTE:
I've got a Netgear WGR614 and Feisty recognised it no trouble and setup the whole works except for the bit done by Netgear.
try this; -
HTML Code:

 [http://www.routerlogin.net/start.htm](http://www.routerlogin.net/start.htm)

It worked well for me and I'm just a beginner.

-------------------------------------------------------------------------------------------------------------------------

THIS PAGE NOT AVAILABLE ON THE NETGEAR SUPPORT SERVER

------------------------------------------------------------------------------------------------------------------------

One machine at a time, as I said. 
First, how do I know this is working as a wireless router and I'll be able to connect to it?
Second: If I were to want to make an actual wireless home network with the router, would it work as is?

Thanks in advance. Please speak NUBIE UBUNTU

Pffester

---

