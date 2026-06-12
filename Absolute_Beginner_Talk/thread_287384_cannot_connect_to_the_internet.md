---
title: "cannot connect to the internet"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by albert 12 on 2006-10-28
I have built a new computer as I have decided to move to Linux, as I have no intention of moving to Vista.
The specs are as follows
AMD 64 3500 processor
2 X 512 DDR3200 Kingston memory
160gb Seagate IDE drive
160gb Maxtor  IDE drive
Nvidia 6600Gt graphics card
Antec 400 watt truepower PSU
Pioneer DVDRW
Floppy.
I installed Ubuntu 6.06 Dapper Drake, there were no problems with the install and when i tried to connect to the internet, it failed.
I rang a friend and he told me to run lspci & /sbin/ifconfig, and then find a forum and post the results.

Here are the results, I hope you can help me.
I tried Knoppix and that would not connect to the internet either.

0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
trackrat@alan2273:~$

trackrat@alan2273:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:E6:50:D4:53
          inet6 addr: fe80::216:e6ff:fe50:d453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:501 (501.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1556 (1.5 KiB)  TX bytes:1556 (1.5 KiB)

Thanks in anticipation.

I forgot to say the computer is connected to the internet through a D-Link router which is hooked up to a cable modem.

---

### Post by featherking on 2006-10-28
How are you connecting to the internet? Cable/Dsl? Are you going through a router? Another place you can check how your connection is set up is by going to System>Administration>Networking. This is basically a gui for the ifconfig command. Here you can setup static IP or disable/enable devices. Without more info its hard to say what your problem could be.

lspci and ifconfig are listing your network adapter so that tells you at least the driver in ubuntu is functioning properly. So not being able to access the internet probably is a problem with your setup. If you are connecting to a router can you ping the router? or can you ping your Cable/Dsl modem? 

You see why more info is needed. If you tell more about your setup, we can help troubleshoot more to get it up and running

---

### Post by woedend on 2006-10-28
is dhcp set up from the router end?  it appears to be detected, obviously, but not pulling anything.  What messages do you get when you run sudo /etc/init.d/networking restart.

try connecting to 192.168.0.1 or .1.1

---

### Post by albert 12 on 2006-10-29
Thanks woedend, the sudo /etc/init.d/networking restart.
 produced a page of text, which I did not understand, but it said failure each time.
Then I tried pinging 192.168.0.1 and it connected to the internet, and downloaded 187 updates.
As I am new to this I will be asking a lot more questions, but I will use the search function before I do.
Thanks.

---

### Post by NeoLithium on 2006-10-29
What type of internet to do you have, as before? Cable/DSL, do you need a username/password to connect to your ISP?

---

### Post by albert 12 on 2006-10-29
I use a D-Link router which is connected to a cable modem, and do not need a user name or password, as it is always on.

---

### Post by Bartender on 2006-10-29
I'm not a networking guy, so please forgive me if this is a lame suggestion.  Would it make any sense to connect directly to the modem and try again?  Eliminate as many variables as possible and work back from there?

---

### Post by albert 12 on 2006-10-29
Bartender as I said in the post a while ago, my internet is now working thanks to a suggestion from woedend, but thanks for your input.

---

