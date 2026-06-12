---
title: "Scary World of Ubuntu: Please help with wireless"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by satkin2 on 2007-01-30
Hello,

I've just installed Ubuntu onto my laptop and am now trying to get everything I want set up.

I'm trying to set my internet connection, but I don't know where to begin.

I'm running the Ubuntu 6.10.  The wireless card in the laptop is according to windows xp device manager is HP WLAN 54g W450 Network Adapter.  I've looked in the device manager on Ubuntu and saw all kinds of stuff so I'm not sure if it recognised it.

I've looked on posts and seen that it's quite complicated to set up if your a newby so any help would be really appreciated.

Thank you

Steve A

---

### Post by sonny on 2007-01-30
You are a little vague with your description of the problem... as I undersootd you are tryng to get your wireless working.. you need to know what is the "chipset" of your wireless card, but in general you can follow [this]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") how-to to get it working, don't be sacare of the terminal, it's more userfrendly than you think.

---

### Post by dexter on 2007-01-30
Do you see your wireless network card listed in System->Administration->Network ?

---

### Post by satkin2 on 2007-01-31
Hi

Dexter,
when i go to networking, wireless connection has no tick, and the properties are empty, so i don't think it's finding the card.

Sonny,
I'll have a look through the link and report back.

Thanks to both of you.

Steve

---

### Post by satkin2 on 2007-01-31
[FONT="Courier New"]Hi

I've looked through the tutorial and looked through a number of other forums, how to's etc.

It appears I'm using a Broadcom 4306 Chipset, which people have problems with, but I've not been able to find a solution.

I've seen on various sites to run iwconfig and should look for wlan0.  I don't get this on my results.  :( 

I get

> 
**lo        **no wireless extensions

**eth0      **no wireless extensions

**eth1**
IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4306"
Mode: Managed  Frequency=2.437 GHz  Access Point:  Invalid
RTS thr: off  Fragment thr=off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

**sit0      **no wireless extensions
[/FONT]

As I'm 100% new to linux all of these codes are going way over my head, :confused: so I don't know if there is something really obvious or not, I don't even know if this is the information that is needed most.

Any help would be appreciated.[-o<

---

### Post by Brunellus on 2007-01-31
> **satkin2 said:**
> [FONT="Courier New"]Hi

I've looked through the tutorial and looked through a number of other forums, how to's etc.

It appears I'm using a Broadcom 4306 Chipset, which people have problems with, but I've not been able to find a solution.

I've seen on various sites to run iwconfig and should look for wlan0.  I don't get this on my results.  :( 

I get

[/FONT]

As I'm 100% new to linux all of these codes are going way over my head, :confused: so I don't know if there is something really obvious or not, I don't even know if this is the information that is needed most.

Any help would be appreciated.[-o<
good news:  your card is detected and seems to be working.  

Your wireless card is 

eth1 

please post the output of 

ifconfig eth1

and 

iwconfig eth1

or alternatively you could set it up using the 'networking' tab in System>Administration.

---

### Post by satkin2 on 2007-01-31
Hi Brunellus, here's the output from the commands.

**ifconfig eth1**
eth1      Link encap:Ethernet  HWaddr 00:90:4B:42:E1:39  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 

**iwconfig eth1**
eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I couldn't see how to do it through the menu system.

Thanks

Steve

---

