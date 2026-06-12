---
title: "Ubunti Wifii"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by wolfdreamer on 2007-05-03
Hello,

        Ive gotten ndiswrapper working (i think??) on my fresh install of Fiesty Fawn. The problem is I cant connect to any network. I ran dhclient wlan0, and it didnt do anything I ran wifi radar and it doesnt show any networks. When I run 'ndiswrapper -l' it says driver insalled device present.  Also when I run the network tools app from the system menu It shows two devices wlan0 and wlan0:avahi, the second of which comes up with an IP, wlan0 doesnt show any ip. What am I missing??

---

### Post by teddybairs1 on 2007-05-04
What's your wifi card? Mine is a Broadcom 4318. Are you running Ubuntu or Kubuntu? What does Network tools say? Are you getting an ip address?

---

### Post by raxiux on 2007-12-26
i have the exact same problem.  I have a dlink 630. I can see the ap s but cannot connect to them, "network tools" show two different interfaces wlan0 and wlan0:avahi, wlan0:avahi shows some activity under "interface statistics" and interface information shows it active, but when I click on configure it says "the interface does not exist" . Under network settings, the interface which I can see the ap s is indeed wlan0. so installing the driver with ndiswrapper creates 2 interfaces which conflict each other. anyone know any workaround for this?

---

### Post by nick_h on 2007-12-27
You may have to blacklist the native driver when using ndiswrapper.

What is the output of:
```
iwconfig
```
?

---

### Post by merlin666 on 2008-01-04
Same problem here, maybe it's this alternate bcm43xx driver that I can't get rid off (despite blacklisting):

rolf@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rolf@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:15:5F:EB  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe15:5feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2625133 (2.5 MB)  TX bytes:393331 (384.1 KB)
          Interrupt:23 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:8C:F9:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:d0000000-d0002000 

wlan0:ava Link encap:Ethernet  HWaddr 00:90:4B:8C:F9:E7  
          inet addr:169.254.11.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:d0000000-d0002000 

rolf@ubuntu:~$ ndiswrapper -l
netbc564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by wolfdreamer on 2008-01-26
Ive spent a lot of time with this wireless card both with Ubuntu, CentOS, and Fedora. Ive come to conclusion that is just not supported both with MadWIfi and ndiswrapper. Ive switched to using Ubuntu 7.10 with a Linksys WMP54G gotta go with standards sometimes. 

The card I was using was the one bundled with my HP m7480n desktop pc. It used an Atheros chipset.

---

### Post by dwhan8608 on 2008-02-14
I'm quite a ubuntu noob, but i had the exact same problem and solved it today...
not sure if it'll be helpful..and i dont even know if it's just for my computer or everyone's...but here it goes anyways.

first of all, do you guys have bluetooth device?
ever since i activated my bluetooth preference, it seemed to have that problem.
i had gusty installed recently and did not configure my bluetooth mouse while i was browsing the web, and suddenly it got disconnected.
and i later realized when i do "iwconfig" it lists two wlan....
wlan0 and wlan0:avahi
i didn't know what avahi was but i did

sudo ip link set wlan0:avahi down

and wlan0:avahi went down and became unknown..
and i just disabled wlan0 and enabled it again using System->Administration->Network
and it found the correct ip...
hope this helps...

---

### Post by pro-rsoft on 2008-02-18
Awesome, that worked for me! Thanks!

---

### Post by kurbads on 2008-03-18
I also have the same both wlan and wlan:awahi with strange IP address, but when I try "sudo ip link wlan0:avahi down" it says "wlan:awahi" is unknown. If I type "sudo ip link show wlan0:avahi" it shows mac address of wlan0.

Oh! No, I forgot the "set" statement...

Now it does not show any wlan device!

It shows again wlan0 after restart, but still can't connect. I try enabling security, disabling... no luck. Ubuntu sees if secrity is enabled, even displays pasword window, I set both Open type 128bit WEP Encryption security on both sides, but it does not connect.

In Vista tryal preinstalled on the same notebook, OS connects to wireless without an effort.

---

### Post by fmouse on 2008-06-23
I've had similar problem here on my Dell D600 laptop w. a Broadcom wi-fi card after an upgrade from Gutsy Gibbon to Hardy Heron.  Turns out I got blindsided by thinking the solution was out at the bleeding edge.  The Dell has an internal switch in its BIOS, toggled by the Fn-F2 key combination, which turns this card off and on.  Somewhere in the upgrade this switch got flipped, probably by software.  More likely, since Linux overwrites the native BIOS, this switch is emulated in the Linux kernel and it was off by default at startup in the new kernel.

Now if I can only get the (barely functional!) Gnome Network Settings app to work I'll be back to square one.

---

