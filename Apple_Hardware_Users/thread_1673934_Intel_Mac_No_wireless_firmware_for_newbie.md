---
title: "Intel Mac No wireless firmware for newbie"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by gamertroll on 2011-01-23
I have a Intel Core Duo 2.53GHz Macbook Pro. I run Snow leopard, vista and ubunto 10.10. I just installed ubunto and do not have any previous experience with Linux. Please note that I do not have access to a wired internet connection. I am currently posting to this forum through Vista on the same machine using the wireless connection. Connecting to a wired connection will not be available to me due to where I am and the situation I am in. I am currently in Kuwait and it will be a few months until I have access to a wired connection back in the states. I have searched the forums for answers, however I don't fully understand what they suggest. I will outline my progress so far... 
First, i did check the power management feature on the driver inside Vista to make sure it was set to disable. 
Then I made an attempt at installing NDISWrapper-utils-1.9.deb. I downloaded this in Vista and moved it to my desktop in Ubunto. When I double click it I get this error message: Dependency is not satisfiable: ndiswrapper-common
 
Also, for refernce, the driver I have in Vista is BCMWL6.
 
I ran some terminal commands and they are listed here...
```
tim@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
 
tim@ubuntu:~$  iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
 
tim@ubuntu:~$ sudo lshw -C network
[sudo] password for tim: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:26:xx:xx:xx:xx
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:43 memory:d3486000-d3486fff ioport:21e0(size=8) memory:d3489000-d34890ff memory:d3489300-d348930f
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:23 memory:d3200000-d3203fff
 
tim@ubuntu:~$

```
I am not going to understand quick answers of uninstall and reinstall. This is my first linux attempt. Please provide details. I have tried looking through the forums. I am sorry for reposting an issue that seems to run rampant. I did look around and that is how I was able to get this far. However I am stuck since I am unable to use a wired connection, or install files that I download through vista or mac on the same machine. 
 
Also: I dual boot OSX and Vista. When I installed ubunto, I installed it so that when I boot windows, I am asked if I want to load Vista or Ubunto (dual boot option in windows). Ubunto is loaded on a partition on my hard drive, not on an external drive.
 
I have tried to give the most information I can up to this point. Hopefully its enough for somebody to guide me in the right direction. I am excited to start exploring Ubunto.
 
Thanks in advance and sorry again if I'm beating a dead horse by posting for help on this topic.
 
edit: I am using rEFIt only for the booting process.

---

### Post by ArtificialMusik on 2011-01-23
I, as well, have this issue. I am running a Macbook Pro 6,2. I have access to a ethernet connection and it is the only connection that works. (so that means one out of two of the drivers loaded correctly.) I am also a noob when it comes to using Ubuntu or Linux period. I honestly have no clue but would love to discover.
I installed a recommended driver for wirelss over ubuntu and it seems to not work. :(
I hope this thread gets some more hits with people interested in helping because I would really prefer to be using Ubuntu over Windows hogging OS. Thank you.
Edit:: My MacbookPRo is model 6,2

---

### Post by gamertroll on 2011-01-24
I was able to get ndiswrapper installed, however I can't seem to find the .inf file for the driver. I am using Vista and have the .sys version that I tried to unpack. That didn't work. I have been looking on the internet but haven't been able to locate the .inf file. I am hoping this works for me. Where is a good location to download .inf files? I am looking for the BCMWL6.inf file if possible.

---

### Post by gamertroll on 2011-01-24
So I found a copy of bcmwl5 and downloaded it. ndiswrapper tells me - no device. I tried to restart and see if that changed anything, but nothing is working yet :( Not sure where to go.
any help please?

---

### Post by ronbirrell on 2011-01-25
Hi all, I have a MBP 5.5 running osx 10.6.6 and Ubuntu 10.10.  To achieve wireless connectivity from ubuntu using the bcm4322 hardware I did the following:

Start Ubuntu
Select system, administration, additional drivers
Select Broadcom STA
Choose activate
Close

Select system, preferences, network connections
Select wireless tab
Add or edit a wireless connection
At the bottom of the respective screen make sure a tick is in the box marked "available to all users"

Reboot computer twice or three times.  Connection should be established.

---

### Post by gamertroll on 2011-01-25
can they be located anywhere or do they need to be in a certain folder? I am downloading them now and will try shortly. If it works, I will post back. I also am using a macbook pro 5,5.

---

### Post by ronbirrell on 2011-01-25
does the STA driver show up in additional drivers?

---

### Post by gamertroll on 2011-01-25
they do not show up in additional drivers. however I have this now...

[CODE]*-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3200000-d3203fff
tim@ubuntu:~$ 
/CODE]

That means I'm getting closer,right?

---

### Post by ronbirrell on 2011-01-25
Getting closer, here is a copy from my laptop

rbirrell@rbirrell-MacBookPro:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:25:bc:e0:42:86
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:43 memory:93486000-93486fff ioport:21e0(size=8) memory:93489000-934890ff memory:93489300-9348930f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:25:00:4c:8d:36
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:23 memory:93200000-93203fff

---

### Post by gamertroll on 2011-01-26
I can't seem to get any further. What do I have to do in order to get the driver to show up in Additional drivers? I really wish I had ethernet access

---

### Post by gamertroll on 2011-01-29
Ok so I was able to find all the dependencies to load the Broadcom STA off the Broadcom website. I used the newest driver and did the build. Everything works great! My only problem is, how do I get this to load at startup? Right now, everytime I boot I have to insmod to get it to work.

---

