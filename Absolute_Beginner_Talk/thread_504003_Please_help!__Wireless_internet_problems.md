---
title: "Please help!  Wireless internet problems"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by lalimalina on 2007-07-18
Yesterday, I downloaded and installed Ubuntu 7.04 on my computer.  I installed it so that it takes up the entire hard drive; Windows is no more.  I have an entire set of Windows backup disks, but I hope not to need them.

One of my issues is that I do not have internet of my own.  Instead, I take my laptop to various cafes and bookstores that have free wireless internet.  With Windows, all I had to do was pull up my wireless network settings, and Windows would search for any available wireless networks then provide me with a list to choose from.  Ignorantly, I assumed that Ubuntu would work the same way without really researching it.

I have tried using the troubleshooting guide, but frankly, I don't understand it.  I am not computer savvy in the least -- I don't know what wireless routers and drivers and cards are, or how they work, or which ones I have, if I have any.  I don't know how to find out.  I tried entering one of the commands to find my wireless driver in a terminal, but did not understand any of the data that popped up.  (I'm sorry, but the terminal will not let me scroll in either direction to see the command, and I cannot refind the webpage I got the command off of, so I'm not certain what command I used.)

I have tried going to System --> Administration --> Network.  In the connections tab, the three items are Wireless Connection, Wired Connection, and Modem Connection.  The checkbox by Wireless Connection has a dash (-) through it, instead of a checkmark like the box by Wired Connection.  The Modem Connection also has a dash through its checkbox.  Underneath Wireless Connection, it says "Roaming mode enabled."  (I have tried using my connection with roaming enabled and disabled.)

When I go to the properties for the wireless connection, it does not have a box to enable to connection.  The only checkbox is to enable or disable the roaming mode for the wireless network.  When I enable the roaming mode, all my options go blank and unchangable.  When the options are available, I do not know what to put in the boxes, since I do not have my own internet connection.

I have also tried clicking the network connection in the top right-hand corner of my screen and selecting the option "Connect to Other Wireless Network," then entering the name of the one wireless network I remember.  It does not find the network.  Sometimes it shows two circles with a blue line drawing a connection around them over and over, then reverts back to the picture of the two computers.  Sometimes it shows a set of bars, much like the bars for cell phone service, but they are all blank, like there is no service, even though I know that it should be at full service for the wireless network in that location.

I am sorry I cannot provide more information.  If you will let me know what other information will help, and how I can locate what you need, I will do my best to get it as soon as possible.  I am having to drop by the library to use the internet here, but I will respond in as timely a fashion as possible.

Thanks in advance!

---

### Post by Inxsible on 2007-07-18
Keep the roaming mode enabled. Then single click on the computer icon near the system clock. That will list all the available wireless networks around you, provided you have your wireless switched on. Select the one that you know is free from the cafe. It most likely wont have any security enabled on it.

You getting the bars --atleast sometimes-- means that your wireless card works. Maybe the signal is too weak. :(

Hope that helps !

---

### Post by lalimalina on 2007-07-18
When I single click the icon, it does not list any networks.  When my mouse hovers over it, it says "no network connection."

It does this even when I am in a building with multiple free networks that I used to pick up at full signal with Windows.

Thank you for your quick reply!

---

### Post by ugm6hr on 2007-07-18
Might be a problem with driver support:
In Terminal:
```
lspci
```
That's lower case LSPCI
You are looking for Ethernet / Network controller information (post it back here or search these forums).

Other useful info:
```
iwconfig
ifconfig
```

It will be difficult if you have to go back to the library each time - perhaps take your laptop with you to the library?

---

### Post by lalimalina on 2007-07-18
When I type lspci, these lines pop up (with many, many others)

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.
llg Wireless LAN Controller (rev 02)


When I type iwconfig, this is what pops up.

lo                    no wireless extensions.

eth0               no wireless extensions.

eth1               IEEE 802.11b/g  ESSID: " "    Nickname: "Broadcom 4318"
                      Mode:Managed    Access Point:  Invalid
                      RTS thr:off     Fragment thr:off
                      Link Quality=0/100  Signal level=-256 dBm    Noise level=-256 dBm
                      Rx invalid nwid:0   Rx invalid crypt:0    Rx invalid frag:0
                      tx excessive retries:0    Invalid misc:0    Missed beacon:0


When I type ifconfig, this is what pops up.

eth0               Link encap:Ethernet   Hwaddr 00:E0:B8:91:98:D2
                      UP BROADCAST MULTICAST  MTU:1500   Metric:1
                      Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:0 errors:0 dropped:0 overrums:0 carrier:0
                      collisions:0 txqueuelen:1000
                      RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
                      Interrupt:11

lo                   Link encap:Local Loopback
                      inet addr:127.0.0.1
                      inet6 addr:  ::1/128 Scope:Host
                      UP LOOPBACK RUNNING   MTU:16436  Metric:1
                      RX packets:20 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
                      collisions:0 txqueuelen:0
                      RX bytes:1432 (1.3 KiB)   TX bytes:1432 (1.3 KiB)

Sorry, I posted a little early to begin with!  What does all this mean?

---

### Post by ugm6hr on 2007-07-18
> **lalimalina said:**
> 02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.llg Wireless LAN Controller (rev 02)

This is the problem - your chipset for wifi is not supported as default....

Try this - 2 options available - detailed here:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by lalimalina on 2007-07-18
I'll give this a try tomorrow; time on the library computer is up.

Thank you so much for helping me identify the problem!!!

I'll let you know how it works.

---

### Post by lalimalina on 2007-07-20
When I first tried this, it worked perfectly.  All I had to do was install the first application, and I had no problem connecting to a nearby wireless network and browsing the internet.

However, now it lists all the available networks and their signal strengths, but will not connect.  When I click on one, it shows the blue loopback while it attempts to connect, then reverts back to the two computers with no network connection.

Any idea why it does this?

---

