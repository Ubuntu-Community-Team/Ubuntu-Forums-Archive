---
title: "[SOLVED] Help Connecting to External Hard Dive Via Ethernet Port"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-08-19
I have my WD my book world edition connected to a linksys wireless g router that is connected to my computer. Does anyone know how I can map a network drive to the external hard drive so I can access it? I know next to nothing about networking.

---

### Post by nexu56 on 2007-08-20
Try going to Places menu -> Network and see if it pops up there.

---

### Post by cwrann on 2007-08-20
All I have under network is an Icon called "Windows Network that I did not set up or put there, it was always there. Their is nothing inside the folder. I have attempted to do some tweaking in an aplication that mentions networking but have had no luck.

---

### Post by nexu56 on 2007-08-20
Can I confirm your setup... your WD box conencts to the router via a cable, and your pc connects to the router via wireless?

What is your network address range? If you're not sure what I'm talking about, just type "ifconfig" in a terminal and paste the results.

---

### Post by cwrann on 2007-08-20
both my PC and my WD connect via cable to the same router

---

### Post by cwrann on 2007-08-20
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1A:92:F0:19:1A
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fef0:191a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:53177330 (50.7 MiB)  TX bytes:9542166 (9.1 MiB)
          Interrupt:23 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:1A:92:F0:26:FA
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:965408 (942.7 KiB)  TX bytes:965408 (942.7 KiB)

---

### Post by nexu56 on 2007-08-23
So your PC lives in the 192.168.1.* range. You will need your WD drive to have an IP address in the same range to be able to talk to it.

You can use nmap to look for other devices in the same range as you. Install nmap:

> sudo apt-get install nmap

then run the following:

> nmap -sP 192.168.1.0/24 |grep up

It might take a few minutes to complete so please be patient.

---

### Post by cwrann on 2007-08-23
this is what I get from nmap:

nmap -sP 192.168.1.0/24 |grep up
Host 192.168.1.64 appears to be up.
Host 192.168.1.102 appears to be up.
Nmap finished: 256 IP addresses (2 hosts up) scanned in 2.471 seconds

I'm not sure what to do with this information.

---

### Post by nexu56 on 2007-08-23
Hmmm, those two addresses both belong to your PC. It hasnt found the address of your WD drive.

I'm sorry, I can't think of much else at this point. Anyone else?

---

### Post by cwrann on 2007-08-26
Thanks for your help I'm trying my luck with the folks at launchpad, I guess I was the only person in the world that was suckered into getting My Book World edition. (didn't even work well in XP). But I was depending on it for a full ubuntu conversion.

---

### Post by cwrann on 2007-08-27
I figured it out!!!
For some reason I set the my Eth0 port that is connected to my router to static IP. I reset it to DHCP plugged the hard drive into the router and hit browse in Connect to server. Simple!

Way easier than it was to use in XP when I had to download software and use the mionet service.

thanks for all your help.

---

### Post by nexu56 on 2007-08-29
Congrats!! Glad you got it sorted out.

---

### Post by Mongo5000 on 2007-10-31
I just bought a mybook world edition 2 and ubuntu seemed to find it in the windows network with my ubuntu set to static.

Now trying to figure out the permissions trouble... ugh

---

