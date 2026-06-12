---
title: "[SOLVED] no internet connection not working"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by faytaliti on 2008-03-15
I am a newbie here. My internet connection doesn't seem to be working - no web pages opening! I read a few other threads and saw "DNS" popping up here and there so I checked it out and it seems to be OK & there is a number similar to IP address in it. I have an broadband ( ADSL ) connection and I use a router which has wi-fi capabilities. But the router is connected to my pc via an Ethernet cable. Please bear with me as I am clueless here :confused: . Also I am getting really impatient. So please help!!!

---

### Post by Omnios on 2008-03-15
Hi I had a similar problem with my old tower. The connection was set up and looked bood but could not connect so I did tne following. I right clicked the net connect applet and turned it off. Then I opened the terminal and used.
 
```

sudo ifconfig eth0 down
sudo ifconfig etho up
sudo dhclient eth0

```
 
 This is similar to release and renew in windows.
 
 Also the eth0 is the net connection so if yours if some thing else use that.

---

### Post by stoneybroke on 2008-03-15
Hi, Sometimes you might have to re-set connection on Ubuntu click on the 2 tv screens on the top right hand corner and turn it off then on again and see if that cures your problem

---

### Post by faytaliti on 2008-03-15
:KS thanks man Ill try it out

---

### Post by Iowan on 2008-03-15
Under the "Manual configuration" icon in upper right corner, check the "Wired Connection" Properties to see what type of connection you have set up.

---

### Post by PapaNerd on 2008-03-15
Let's break this problem in two.  Suggest you bring up a terminal window (Applications > Accessories > Terminal) and do the following two commands:
ping ubuntuforums.org
ping 91.189.94.186

If the first command does not work, and the second does, then DNS is likely not resolving for you.  If the second does not work, then we can go after the connectivity issue by itself.

---

### Post by ugm6hr on 2008-03-15
Some information would help.  The ouput from these commands:

```
lshw -C network
ifconfig
route
```

---

### Post by Papa-san on 2008-03-15
Just in case you didn't know... DNS is the program that 'trades' a numeric IP into the
 www. blahblah .com that we are all so familiar with.

---

### Post by faytaliti on 2008-03-16
:KS I typed the following in the terminal

```
lshw -C network
ifconfig
route
```


this was the output : -


```
faytaliti@kronos-studio:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:52:2d:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.2 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
faytaliti@kronos-studio:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:52:2D:0E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe52:2d0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3494 (3.4 KB)  TX bytes:10716 (10.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

faytaliti@kronos-studio:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         WA1003A.Huawei  0.0.0.0         UG    100    0        0 eth0
faytaliti@kronos-studio:~$ 
```


:-k   so any further sugestion to rectify the problem
       Oh by the way.............. I am getting really impatient!!!!! :mad:

---

### Post by ugm6hr on 2008-03-16
Try this:
[http://ubuntuforums.org/showpost.php?p=4522099&postcount=2](http://ubuntuforums.org/showpost.php?p=4522099&postcount=2)

Looks like you are connected to the router, and have an IP address assigned.

---

### Post by whose.down@gmail.com on 2008-03-16
why don't u ask ur ISP for details to be entered on the "2 monitors" icon? this is what worked for me.

---

### Post by PapaNerd on 2008-03-16
faytaliti:  We can all understand you being "really impatient" (as you say), but you still haven't given those of us trying to help enough debugging info.  So far, from the info that ugm6hr requested, we can tell that your network card seems to be working and that you have received a dhcp address from your modem or router.  What we do not know is if your data packets are getting out to the world, or if DNS is resolving, which is what the output from the two ping tests would help tell us.  Can you do those commands?  Also, if you could post the output from the "nslookup ubuntuforums.org" command, it would also help us.

---

### Post by Ptero-4 on 2008-03-16
Also. try typing in whatever browser you use the IP address of the ADSL modem/router your ISP gave you and then click cancel at the login box that your browser pops up. This does a software reset on the modem/router and sometimes fixes this stuff.
(the tech support guy at my current ISP gave me this tip for when the ADSL modem windows up and need to be rebooted).

---

### Post by faytaliti on 2008-03-19
:KS Thanx that worked just fine :popcorn:

---

