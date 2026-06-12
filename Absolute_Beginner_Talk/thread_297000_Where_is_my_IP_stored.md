---
title: "Where is my IP stored?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-10
I have been trying to get my wireless to work with my new, verizon supplied wireless router. The IP for this router is 192.168.1.1

My old linksys router was designated 192.168.2.2

Now, when I try to configure my wireless through the 'Network' GUI, It is supposed to be as simple as putting in the ESSID, the WEP password, and clicking on DHCP. In theory, it should be working just fine, but it isn't.

The problem is that wherever the old IP was saved, is still looking for that old IP. when I run ifdown eth1, I get this:```
john@laptop:~$ sudo ifdown eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on   LPF/eth1/00:90:4b:2c:52:6b
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.2 port 67
john@laptop:~$

```:( 

I am hoping someone can help me locate where this is, and how to edit it to reflect the proper IP.

---

### Post by dbott67 on 2006-11-10
What have you done with the old router?  Is it still being used or did you unplug it?

The 'released' IP will go back to the DHCP server that issued it (even if you have a new router).  If you request a new IP, what happens:
```
sudo ifup eth1
```
```
suod dhclient eth1
```

If you're still having troubles, post the output of the following commands:
```
cat /etc/network/interfaces
```
```
ifconfig -a
```

-Dave

---

### Post by Papa-san on 2006-11-10
The old router is in a box in the attic. ```
john@laptop:~$ sudo ifup eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on   LPF/eth1/00:90:4b:2c:52:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
john@laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on   LPF/eth1/00:90:4b:2c:52:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
john@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.43  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7297 errors:0 dropped:0 overruns:1 frame:0
          TX packets:4376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2587797 (2.4 MiB)  TX bytes:703462 (686.9 KiB)
          Interrupt:11 Base address:0xcc00

eth1      Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:f8ffc000-f8ffe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3088 (3.0 KiB)  TX bytes:3088 (3.0 KiB)

john@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:4E:F7:A9
                    ESSID:"06B408770040"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-30 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

john@laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid 06B408770040
wireless-key XXXXXXXXXX
auto eth1

iface eth0 inet dhcp

auto eth0

john@laptop:~$

```

---

### Post by dbott67 on 2006-11-10
Just a couple of things to try while I mull over what's happening:

A. It could be the router and/or modem acting goofy.  Try the following:
> 
1. Power off router
2. Reset / power off cable/DSL modem thingy
3. Power on cable modem thingy
4. Wait until the lights stop blinking & what-not
5. Power on router
6. Wait a minute or so
7. Try commands from above in Ubuntu.

B. It could be WEP encryption that's causing the problem.  Normally, I recommend disabling encryption to eliminate WEP as the problem.  Disable it on the router & remove the 'wireless-key' line from /etc/network/interfaces and try to connect.  If you are able to connect, then we can focus on WEP.

**_Re-enabling WEP:_**

If you are able to connect without WEP, try turning it back on in the router and use 128-bit encryption with a simple 13-character password (such as 'wepencryption')

In your **/etc/network/interfaces** try changing the line to:

```
wireless-key s:wepencryption
```
The preceding 's:' idicates that the key is in plain ASCII text & should be 13 characters long (assuming you're using 128-bit).

'sudo ifdown eth1', 'sudo ifup eth1', 'sudo dhclient eth1' and see what happens.

If it works, then change the WEP key to something more difficult and repeat the above steps.


-Dave

---

### Post by Papa-san on 2006-11-10
I'll try that this evening.
I am just concerned that my computer only wants to look for 192.168.2.2. I cannot even get it to try the right one.

Will I have to change the router settings to disable the WEP key? Also, how will this affect the windows systems that are having no problems with it as is?

---

### Post by dbott67 on 2006-11-10
You can also take a look at /etc/dhcp3/dhclient.conf to see if there's anything in that file that's causing the problem.  Here's mine for comparison:
```
dbott@dapper:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by Papa-san on 2006-11-11
etc/dhcp3/dhclient.conf is EXACTLY the same as yours... verbatim...
everything seems to be remarked out anyways. 

The whole router/modem power off/on didn't do anything. (The modem is one with the router. I guess it does both.) I tried to go with an unencrypted setup, but I couldn't connect that way either. 

I am thoroughly convinced that the problem is a latent entry in some system file or something.

---

### Post by Papa-san on 2006-11-11
I found that the channel was different in my ifconfig results, so I changed the router/modem setting to the same (11) Still no good, but I at least know they are the same. And since my ubuntu box has no interface to change this setting, I guess the router interface will have to do! This is really frustrating, as I know that my card is working properly, the router/modem is working properly (it sees me when using the wired connection to it...) I'm able to scan for the signal, and I can read it and get all the particulars, but my system won't pick up the router's MAC addy for some reason... So it won't associate...  Grrrr.

---

### Post by Papa-san on 2006-11-11
I have run through several wiki's and how to's, and have managed to get this far:
```
john@laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:2c:52:6b
Sending on   LPF/eth1/00:90:4b:2c:52:6b
Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPOFFER from 192.168.2.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.2
/usr/sbin/postconf: fatal: open /etc/postfix/main.cf: No such file or directory
cp: `/etc/resolv.conf' and `/etc/resolv.conf' are the same file
run-parts: /etc/resolvconf/update-libc.d/postfix exited with return code 1
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
bound to 192.168.2.45 -- renewal in 32681 seconds.

```
This is the first time anything like this (ifup, ifdown, etc) has even included "eth1" in the same command result as the IP 192.168.2.2. I am not entirely sure, but the "fatal' seems like it might be a problem? Does anyone know anything about the referenced files, and how they might impact my wireless?

---

### Post by Papa-san on 2006-11-12
Well, it is looking like the only thing I am going to be able to do is re-install... I should format to be sure I erase whatever is messing this up? I don't want to install over the top, because it will prolly leave it there. Oh Well! I wonder if this is Open source stuff is really worth it...

---

### Post by dbott67 on 2006-11-12
Just another suggestion.

Can you connect via cable (instead of wirelessly)?  If so, try the following:

1. Connect via cable to the router and see what happens when you perform the steps above (sudo ifdown eth0, sudo ifup eth0, sudo dhclient eth0) and post the output here.

2. If you're still getting errors, try setting eth0 to STATIC IP (as to overwrite the current settings), reboot, surf, make sure everything is working.  If so, try setting it back to DHCP and repeat step 1.

3. If things appear to work properly via wired connection, repeat steps 1 & 2 for the wireless interface (eth1).

-Dave

---

### Post by Papa-san on 2006-11-13
From a fresh reboot, I opened this browser and navigated to this thread through my wired connection to the dsl modem/router.

I did:```
john@laptop:~$ sudo ifdown eth0
Password:
/usr/sbin/postconf: fatal: open /etc/postfix/main.cf: No such file or directory
cp: `/etc/resolv.conf' and `/etc/resolv.conf' are the same file
run-parts: /etc/resolvconf/update-libc.d/postfix exited with return code 1
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.2 port 67
```Then I went to post those results to this thread and got a page loading error (no connectivity, as expected) Then did:```

john@laptop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPOFFER from 192.168.2.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.2
bound to 192.168.2.42 -- renewal in 32657 seconds.

```Then I was again able to post this.
now:```
john@laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:06:5b:e1:ba:40
Sending on   LPF/eth0/00:06:5b:e1:ba:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.2
bound to 192.168.2.42 -- renewal in 37018 seconds.

```

---

### Post by dbott67 on 2006-11-13
I am guessing that your new router is 192.168.2.2... I know from your first post that you said that was your old router & your new one was 192.168.1.1, but it seems to be working.

Can you post the output of:
```
route -n
```

Also, try installing 'traceroute' from Synaptic:
```
sudo apt-get install traceroute
```
and then run a traceroute to google:
```
dbott@edgy:~$ traceroute www.google.com
traceroute: Warning: www.google.com has multiple addresses; using 72.14.205.104
traceroute to www.l.google.com (72.14.205.104), 30 hops max, 40 byte packets
[COLOR="Red"] 1  192.168.1.1 (192.168.1.1)  6.761 ms  0.481 ms  0.705 ms[/COLOR] [COLOR="Blue"]<-- this is the first hop --- my router[/COLOR]
 2  abc.lns-system.ip.execulink.net (209.183.1xx.yyy)  39.974 ms  31.816 ms  33.521 ms
 3  i.core1.ip.execulink.net (209.183.132.97)  29.077 ms  161.228 ms  60.771 ms
 4  static-64-187-25-233.gtcust.grouptelecom.net (64.187.25.233)  23.622 ms  51.884 ms  47.265 ms
 5  GE5-2.WANA-TOROON.IP.GROUPTELECOM.NET (216.18.63.9)  61.253 ms  48.566 ms  56.855 ms
 6  66.59.191.106 (66.59.191.106)  83.516 ms  113.148 ms  86.186 ms
 7  core1-2-2-0.ord.net.google.com (206.223.119.21)  57.004 ms  59.125 ms  41.588 ms
 8  66.249.95.249 (66.249.95.249)  40.724 ms  73.033 ms  54.145 ms
 9  72.14.233.146 (72.14.233.146)  59.176 ms  31.583 ms  32.515 ms
10  66.249.94.96 (66.249.94.96)  34.640 ms  26.447 ms  42.587 ms
11  * * *
12  qb-in-f104.google.com (72.14.205.104)  48.036 ms  59.304 ms  41.349 ms
dbott@edgy:~$ 

```

Also, what happens when you point your browser to 192.168.2.2?  Can you login?  What about 192.168.1.1?

-Dave

---

### Post by Papa-san on 2006-11-14
Hi...

Since none of the Windows systems were having difficulty with the new setup, I decided to change the router's IP to the one my system seemed to want to look for- 192.168.2.2 

This change was handled seamlessly by the win systems, but had no real effect on mine. Currently I am re-installing Breezy...
I had minimal trouble getting that one to set up, so I am going to try it again. The biggest issue I had to deal with was the update feature's insistence that I needed to upgrade to Dapper. Eventually I caved in and updated. This began a five month struggle to get a truly functional Linux box, which never came to fruition. :( 

So... I am going back to what I consider to be the most usable and stable Ubuntu version I have used. I saved all of the irreplacable data on it to some extra space behind my website, so I should be able to get her set up again pretty easily!

Edit: I am downloading edgy, but I'm really edgy about trying to install it if it is going to cause the hardship Dapper did...

---

