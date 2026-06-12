---
title: "Ubuntu 5.10: Wireless internet not working"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by rasmusbp on 2005-11-25
hi everyone,

i'm having problems getting the internet working in ubuntu 5.10. i'm completely new to this world of linux, so I couldn't understand much of what was being discussed on the subject in the "how-to" section.

i'm running a Asus M6N centrino laptop with a built-in intel PRO/SET 2200BG wireless card. There are also a modem and a LAN card, but I don't use them. 

the installation of ubuntu went smoothly, and it looks like i am connecting with my router (Linksys G-Broadband). However, I can't access any websites. Firefox says "whatever.com could not be found...". Clicking on the internet-icon in the system tray in the upper right corner, i can see there is some "activity", and the device switches btw "idle/receiving/sending" constantly. The network is configured with "DHCP" and with WEP encryption.

So, I seem to be connected to my router, but not to the internet. The internet connection is working fine from XP, though, so I must have misconfigured something. I have put my router IP (gateway address) as the DNS address. 

Can someone please give me advice how to make this work?! i'm a complete linux virgin, so please be gentle with replies - I barely know where to find the terminal window. 

Thank you whoever is kind enough to help

All the best,
Rasmus
- who is happy to have escaped the world of microsoft, despite the problem....

---

### Post by onejoy on 2005-11-25
I just installed ubuntu for the first time a few weeks ago, and had quite an ordeal getting the wireless card to work in my laptop as well, but it's working now.

[http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+configuration](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+configuration)

It worked for me.

Hope it helps!

---

### Post by Lambert on 2005-11-25
post the output of the following commands

iwconfig
ifconfig
cat /etc/resolv.conf

try to ping the following 

ping <routers_ip>

ping 216.239.57.99

ping [www.google.com](www.google.com)

Post your results of these pings

---

### Post by rasmusbp on 2005-11-25
Thanks a lot for helping, I really appreciate it! 
Here are the outputs:


**IWCONFIG**
rasmus@rasmus-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Madam Blaa"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:26:3D:DE
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


**IFCONFIG**
rasmus@rasmus-ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:4F:19:04
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe4f:1904/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2412 (2.3 KiB)  TX bytes:1212 (1.1 KiB)
          Interrupt:4 Base address:0x8000 Memory:ff9ef000-ff9effff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:212211 (207.2 KiB)  TX bytes:212211 (207.2 KiB)




**RESOLV.CONF**
rasmus@rasmus-ubuntu:~$ cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No such file or directory
rasmus@rasmus-ubuntu:~$ cat /etc/resolve.conf
cat: /etc/resolve.conf: No such file or direct

NB: The resolve.conf file IS in the etc folder - i don't know why the terminal couldn't find it. Last I checked it, there was only a "nameserver: 192.168.1.1" in there.


**PING 192.168.1.1**
rasmus@rasmus-ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.042 ms

64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.041 ms



**PING 216.239.57.99**
rasmus@rasmus-ubuntu:~$ ping 216.239.57.99
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable


**PING GOOGLE**
rasmus@rasmus-ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by Lambert on 2005-11-26
One last command as you look connected with an ip assigned.  Not being able to ping external site with ip is???

```
route
```

You should have output like this

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0     U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by fuscia on 2005-11-26
edit: post cancelled.

---

### Post by ubuntuuser on 2005-11-27
[QUOTE=rasmusbp]
**IFCONFIG**
rasmus@rasmus-ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:4F:19:04
          **[COLOR="Red"]inet addr:192.168.1.1[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe4f:1904/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2412 (2.3 KiB)  TX bytes:1212 (1.1 KiB)
          Interrupt:4 Base address:0x8000 Memory:ff9ef000-ff9effff

**RESOLV.CONF**
rasmus@rasmus-ubuntu:~$ cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No such file or directory
rasmus@rasmus-ubuntu:~$ cat /etc/resolve.conf
cat: /etc/resolve.conf: No such file or direct

NB: The resolve.conf file IS in the etc folder - i don't know why the terminal couldn't find it. Last I checked it, there was only a "nameserver: **[COLOR="Red"]192.168.1.1[/COLOR]**" in there.


**PING 192.168.1.1**
rasmus@rasmus-ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.042 ms

64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.041 ms



**PING 216.239.57.99**
rasmus@rasmus-ubuntu:~$ ping 216.239.57.99
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable


**PING GOOGLE**
rasmus@rasmus-ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)[/QUOTE]

So it looks like:
a: The adapter you want to use is eth1
b: this adapter has the IP 192.168.1.1
c: you can ping this adapter
d: you can't ping anything outside of your computer

The IP in your resolve.conf has to be your router's IP, NOT your own adapter's IP.

---

### Post by rasmusbp on 2005-11-27
thanks everyone!

well, i did the route command and it looks nothing like the one which Lambert posted:

> rasmus@rasmus-ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
default         rasmus-ubuntu   0.0.0.0         UG    0      0        0 eth1


When I changed the configuration from static IP (which I think was a mistake  since the router is set to give us dynamic IPs using DHCP) to DHCP, I didn't get any output at all:

> rasmus@rasmus-ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

The **resolve.conf** looks like this:
nameserver 192.168.1.1

This is my routers IP.

Thanks again

---

### Post by ren wins on 2005-11-27
i had problems with changing from static IP to dhcp on my computer (among other things)
i finally just gave up and reinstalled (dont do that though)

(i did just break my wifi w/ gtkwifi it seems tho, but i'll make another thread dealing with that)

---

### Post by Lambert on 2005-11-27
What is rasmus-ubuntu? This is usually an ip address of the router that's connected to your internet line. If this is a domain name of the router, not sure if this can/will work:confused:

So you can try this while interface is up

sudo route del default gw rasmus-ubuntu

sudo route add default gw <router ip>

where <router ip> = your router's ip address

Also in your resolv.conf file you should have a line like this.

search hsd1.va.comcast.net

where anything after search is the domain name of the dns server. My complete file looks like this.

search hsd1.va.comcast.net.
nameserver 192.168.0.1


If you have an xp machine connected to the network  you can find your dns server by

start>run...type cmd [enter] then ipconfig /all

Or you can call your isp provider to get details on it.

---

### Post by ubuntuuser on 2005-11-28
Look at the output from ifconfig. There it says:
```
eth1 Link encap:Ethernet HWaddr 00:0E:35:4F:19:04
inet addr:192.168.1.1
```

It looks like your eth1 adapter has 192.168.1.1 as IP. So you better change this IP or the router's IP.

---

### Post by rasmusbp on 2005-12-13
thanks everyone for your comments. in the end, i made the wireless work by reinstalling ubuntu 5.10 and then following (very strictly!) this howto: 

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

paying special attention to always getting the newest drivers from sourceforge. 

cheers

---

