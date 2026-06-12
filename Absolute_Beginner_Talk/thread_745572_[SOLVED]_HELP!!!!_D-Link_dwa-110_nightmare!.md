---
title: "[SOLVED] HELP!!!! D-Link dwa-110 nightmare!"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by IHATEDLINK on 2008-04-04
Hey, I've been desperately searching for a d-link dwa-110 driver or a way to make it work with no luck so far
I switched from XP two days ago so I'm gonna need step-by-step instructions
Thanks in advance

---

### Post by njparton on 2008-04-05
Well if the driver doesn't exist you're probably out of luck.

---

### Post by TeoBigusGeekus on 2008-04-05
Have you tried to connect with WICD?
[http://ubuntuforums.org/showthread.php?t=705391]("http://ubuntuforums.org/showthread.php?t=705391")

---

### Post by Michael.Godawski on 2008-04-05
Can you please post the output of these terminal commands to clarify your current network status?

```
sudo lshw -C network
iwconfig
```

---

### Post by IHATEDLINK on 2008-04-11
WICD?
I don't think it will solve my issue, i mean, the computer doesn't even recognize the damn thingy.

---

### Post by IHATEDLINK on 2008-04-11
description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:88:54:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=10.0.0.6 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s


I am now using a wired network connection.
Please help me!

---

### Post by IHATEDLINK on 2008-04-12
YESSS!!!!
I madee ittttt!!
I was quite simple after all.
I just copied the "driver" folder from the dwa-110 ijnstallation CD onto my computer and then pointed ndiswrapper onto the .inf file, and now it works!!
I'm so happy :)

---

### Post by Mick8882003 on 2008-04-12
please mark as solved

---

### Post by SlappyPappy on 2008-04-12
I love your name. Now that's funny.

BTW I have a D-Link firewire card and it was recognized automagically. 

I don't necessarily love D-Link because of this fact. I think people get way too emotional about tech and whether it works or not. Why get so invested in inanimate objects?

Congrats on your now working D-Link. Ubuntu rulez!  :lolflag:

---

### Post by IHATEDLINK on 2008-04-14
thanks, i couldn't find any other no-taken names :P
and you are very lucky by the way, i mean,recognized "automagically"!!!!
LOL

---

### Post by Petu on 2008-04-26
Hi, I have Ubuntu 8.04 and no network connection, wired nor wireless. I also have DWA-110 and the above solution doesn't work because I don't have ndiswrapper installed, and I have no network connection to download it with :-(
Any idea how I could overcome this? I'm really a newbie with Linux.

---

### Post by peterballard on 2008-05-05
This post is both an answer to the one above, and a request for help.

Hi Petu. I can tell you how I installed ndiswrapper, but I too am stuck:

From the main menu, open
system>administration>synaptic package manager

This should show all packages, alphabetically. Go through the list, until you find 3 packages beginning with "ndis".

Mark them all for upgrade (I think it was a right-click, I forget). 

Then click "install" and it just happens.


Now for the bad news: even when I install ndiswrapper and install the DWA-110 driver, I still can't connect.

I copied the .inf file from the CDROM which came with the DWA-110 onto my hard drive. There were two .inf files (one for Windows XP, one for Vista). I chose the XP version because I am running XP when I am in windows.

I tried installing the .inf file both from the command line ("sudo ndiswrapper -i d_link_dwa_110_cdrom_driver/drivers/winxp_2k_9x/dr71wu.inf") and later I uninstaled and tried installing from the graphical interface (System -> Admin -> Windows Wireless drivers; point to the file and click "Install"); and the install was apparently successful.

But still, when I look at my network using System -> Admin -> Network, there is no sign of my wireless device.

A log of a few network commands (suggested in the Ubuntu help) is below.

```


pballard@sirboris:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:83:28:16
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-2 ip=192.168.0.156 latency=0 link=no module=e1000e multicast=yes port=twisted pair
pballard@sirboris:~$ 
pballard@sirboris:~$ 
pballard@sirboris:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pballard@sirboris:~$ 
pballard@sirboris:~$ 
pballard@sirboris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:83:28:16  
          inet addr:192.168.0.156  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103976 (101.5 KB)  TX bytes:103976 (101.5 KB)

pballard@sirboris:~$ 
pballard@sirboris:~$ ping 82.211.81.158
connect: Network is unreachable
pballard@sirboris:~$ 


```

So how do I get Ubuntu to find my wireless adapter? Any help appreciated.

---

### Post by peterballard on 2008-05-12
Replying to my own post, see the solution at [http://ubuntuforums.org/showthread.php?t=786584](http://ubuntuforums.org/showthread.php?t=786584) , which in turn pointed me to the instructions at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

