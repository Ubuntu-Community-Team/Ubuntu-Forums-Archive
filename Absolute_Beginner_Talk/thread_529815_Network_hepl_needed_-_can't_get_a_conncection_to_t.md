---
title: "Network hepl needed - can't get a conncection to the Internet"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by monkey5672 on 2007-08-19
Hi,

Okay, I need some help. I was finally able to get Ubuntu installed, but now I can't get an Internet connection. 

My set-up:

Cable modem, then into a wireless router. My Ubuntu PC is plugged into that, and my Dell XP Laptop is connecting fine to the wireless connection. 

When I ran Ubuntu Live from the DVD, the Internet connection was working fine. Strange! 

So, what should I check first?

Thanks,

-jm

---

### Post by Happy_Man on 2007-08-19
Are you sure? Try pinging google to check. And then reboot.

---

### Post by HereInOz on 2007-08-19
Possibly a DNS issue.   Try going to System > Administration > Network and set up a static IP address and also enter the IP addresses of your ISP's DNS servers in the DNS tab.

Make sure that the static IP you set up is in the right subnet for your router.

Hope this helps.

---

### Post by monkey5672 on 2007-08-19
Hi,

Thanks for the responses.

Okay, ping to [www.google.com](www.google.com) gives

ping: unknown host [www.google.com](www.google.com)

So, how do I find out my Static IP address, and the proper subnet for my ISP? 


-jm

---

### Post by nitro_n2o on 2007-08-19
if your machine is directly connected to your router you shouldn't have any problems, unless it's connected by usb... 
the subnet is not related to your isp.. if you didn't modify anything in your wireless router, the subnet mask should be 255.255.255.0, but check your router configurations to see.. 
try changing your Ethernet port from the router and see if that makes a difference.. 
and what is the output of ifconfig 
and what is inside /etc/network/interfaces ?

---

### Post by monkey5672 on 2007-08-19
hi again,

one thing i've noticed when playing around with the Network utility:

when i set it to DHCP, I get a failed internet connection. when i set it to Static IP, and put in some info, it seems to try looking up a website, but just times out after a while.

-jm

---

### Post by Lithium17 on 2007-08-19
Is the modem/router connected via a USB cable?

---

### Post by monkey5672 on 2007-08-19
output from more /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath1 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

-jm

---

### Post by nitro_n2o on 2007-08-19
to setup a static address.. 
open /etc/network/interfaces with your favorite text editor 
and put something like this 

```
auto eth0 
iface eth0 inet static
address 192.168.1.26 # most routers start from 100 for dchp so 26 is safe 
netmask 255.255.255.0
network 192.168.0.0 # default to this on most routers class C
broadcast 192.168.1.255 # the last octet should be 255 if using class C
gateway 192.168.1.1 # not crucially important, but not harmful this should be the url to your router iface
```

---

### Post by nitro_n2o on 2007-08-19
> **monkey5672 said:**
> output from more /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath1 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

-jm
 add this to the last line 
iface eth0 inet dhcp

then you are ready to go

keep eth0 on top 
and fix the line below ath0 to iface ath0 inet dhcp instead of ath1

---

### Post by monkey5672 on 2007-08-19
nope, card is not connected with USB, its ethernet cable.

output from ifconfig:

eth0  Link encap:Ethernet  HWaddr 00:0C:76:86:68:07
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets: 0 errors:0 dropped: 0 overruns:0 frame:0
        TX packets: 2115 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b)  TX bytes:24813 (24.2 KiB)
        Interrupt:19 Base address:0x6000

eth0:avah Link encap:Ethernet  HWaddr 00:0C:76:86:68:07
                  inet addr:196.254.4.78  Bcast:169.254.255.255 Mask: 255.255.255.0
                  UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
                   Interrupt:19 Base address:0x6000

lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:637 errors:0 dropped:0 overruns:0 frame:0
      TX packets:637 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:63289 (61.8 KiB)  TX bytes:63289 (61.8 KiB)

-jm

---

### Post by Lithium17 on 2007-08-19
ok, its just that if it was USB, I know of a really good modem manager, maybe they have support for ethernet also, I think it was steveharper.com or something, might wanna take a look just in case.

---

### Post by monkey5672 on 2007-08-19
Hi nitro,

No, that didn't work. same thing .... it just keeps trying to connect, then times out. 


-jm

---

### Post by gb5757870 on 2007-08-19
I haven't really followed what has been done but it appears a recent update has knocked out ethernet connections, so everything that has been suggested is probably in vain.
Check the forums, heaps of people are experiencing this. Hopefully someone in the know is aware!

---

