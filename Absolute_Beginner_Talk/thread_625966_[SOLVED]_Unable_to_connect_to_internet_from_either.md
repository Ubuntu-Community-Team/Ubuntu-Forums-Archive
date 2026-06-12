---
title: "[SOLVED] Unable to connect to internet from either OS with a XP/7.04 dual boot"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by adster101 on 2007-11-28
Help! I have successfully installed ubuntu 7.04 in a dual boot with XP. However, I cannot connect to the internet via either OS! Previously the win XP install was on the internet with no problems. Ipcinfig from the XP install is as follows:

**C:\Documents and Settings\Administrator>ipconfig /all**

Windows IP Configuration

        Host Name . . . . . . . . . . . . : adam
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : Yes

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/100 VM Network Connecti
on
        Physical Address. . . . . . . . . : 00-02-A5-BD-67-DA
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 255.255.255.255

**C:\Documents and Settings\Administrator>ipconfig /all**

Windows IP Configuration

        Host Name . . . . . . . . . . . . : adam
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : Yes

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/100 VM Network Connecti
on
        Physical Address. . . . . . . . . : 00-02-A5-BD-67-DA
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.209.10
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

C:\Documents and Settings\Administrator>

This doesn't look right to me. During the install Ubuntu wouldn't detect/configure the DHCP network so I left it until it was installed.

Now on Ubuntu the Network tools shows thath I am receiving bytes via eth0 but no hardware address is available.
[B]
ifconfig:[/B]

adamrifat@oslicku:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:A5:BD:67:DA  
          inet6 addr: fe80::202:a5ff:febd:67da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:453746 (443.1 KiB)  TX bytes:5172 (5.0 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:02:A5:BD:67:DA  
          inet addr:169.254.9.98  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15888 (15.5 KiB)  TX bytes:15888 (15.5 KiB)

adamrifat@oslicku:~$ 

Also:

adamrifat@oslicku:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
adamrifat@oslicku:~$ 


Why is my ethernet card not responding? Can anyone help, please?

Thanks
A

---

### Post by jryprt on 2007-11-28
I had a similar problem the other day I dual boot also .
I had to call cable co. to reset ip address.
Call them.

---

### Post by civic_si on 2007-11-28
you are getting a windows apipa address that happens when the machine cannot get an ip address from a DHCP server. either you have a bad connection or you need to assign a static address. If you have a linksys router or something giving out DHCP addresses unplug it and plug it back in. that might fix it.

to get the operating systems to get an address use

Windows

ipconfig /release then ipconfig /renew

Linux

ifdown eth0 then ifup eth0

---

### Post by adster101 on 2007-11-28
@jryprt - My other laptop is windows and is connecting to the ISP with no problems. I.e. the laptop I am writing this on! :)

@civic_si - just trying that now....

---

### Post by adster101 on 2007-11-28
I get a timeout when I issue a ipconfig /renew on my windows install. 

Any ideas?

---

### Post by fineas on 2007-11-28
If you don't sharing internet connection, try assign a static ipn as civic_si suggests.Write click on the networking icon on the system tray.Go to properties and select static ip.Give something like 192.168.0.1 .and just click on the subnet mask. This method seems to me the best of all I 've tried.
Other option is this: In a terminal, write

sudo dhclient

---

### Post by adster101 on 2007-11-28
When I do sudo dhclient I get:

blah...
blah..
No DHCPOFFERS received.
No Working leases in persistant database - sleeping.

This connection is working as *this* laptop is plugged into the same modem so it must be giving out a DHCP...?

Also, tried tp put in a static IP with same result.

The weird thing here is that it has taken out the Windows connection as well. Basically looks like the same problem on both OS! Woops.

---

### Post by fineas on 2007-11-28
Ok, things seems to be difficult. Maybe the problem is about something else:confused: , but if you don't bother try these (cheap) tricks that worked for me.These are what I used to do when were losting my internet connection on both ubuntu and XP, before finding the static IP tricks etc..My ifconfig outputs were similar as yours.

We want a message that "connection is enabled" or something like this.So:
In the way you put the static IP, put DHCP. Make sure that, in the corrections tab, eth0 is ticked. Wait for one or two minutes. 
If not successfull, try untick and retick eth0 in the connections tab.Repeat 4 or 5 times.
"sudo ifdown eth0", then "sudo ifup eth0" as suggested in manual

Last trick, "sudo dhclient"

I 'll be happy if any of these tricks help.Good luck:KS

---

### Post by adster101 on 2007-11-29
Things are still not working! :(
I tried:
"sudo ifdown eth0", then "sudo ifup eth0" as suggested in manual

but still get the same result as above.

I am a little confused with your instructions below:
*In the way you put the static IP, put DHCP. Make sure that, in the corrections tab, eth0 is ticked. Wait for one or two minutes.*

I can only choose eth0 in the Network Tools application. If I choose DHCP then I cannot manually configure an IP Addresss. The option is not active. Does that make sense? 

This is an odd problem as the same fault persists in XP. Can the ubuntu installer reconfigure the netowrk card in such a way as to make it useless?

---

### Post by fineas on 2007-11-29
> **adster101 said:**
> 

I am a little confused with your instructions below:
*In the way you put the static IP, put DHCP. Make sure that, in the corrections tab, eth0 is ticked. Wait for one or two minutes.*

I can only choose eth0 in the Network Tools application. If I choose DHCP then I cannot manually configure an IP Addresss. The option is not active. Does that make sense? 



Yes,my fault ](*,)
We check DHCP in order not to manually configure the IP address:). It 's the DHCP server that we expect to give the IP address we need. 


> **adster101 said:**
> 

This is an odd problem as the same fault persists in XP. Can the ubuntu installer reconfigure the netowrk card in such a way as to make it useless?


Most possibly, if ubuntu was able to do this, you wouldn't have internet connection problems :), but I can't swear about this (I'm not a network professional). During installation process, ubuntu tries to use the existing settings, not to change them.

---

### Post by adster101 on 2007-12-01
Well it would appear as though the installer has wrecked the setup of the network card on the laptop. I guess so otherwise the problem wouldn't be on both operating systems.

Anyone got any ideas?

---

### Post by linuxonbute on 2007-12-01
Do you have an adsl modem or a modem/router?

Are you trying to get the dual-boot machine to connect while your laptop is connected?

> 

ifconfig:

adamrifat@oslicku:~$ ifconfig

eth0:avah Link encap:Ethernet HWaddr 00:02:A5:BD:67A
inet addr:169.254.9.98 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

This inet address 169.254.9.98 is a public address. I doubt your ISP allows you more than one active address
unless you have paid extra. What this means is that only one PC can connect at a time.
To use more than one you need a private network within your home with NAT to allow you to share the IP address your ISP supplies.
You cannot just choose your own public addresses.

try 
```

 netstat -r

```
You should get an output like this:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

---

### Post by adster101 on 2007-12-01
It is a motorola sb5100 cabel modem.

I have another computer using the connection but I only ever have one connection at at time,.

I.e. to check the ubuntu connection I will unplug this one and plug the cable into the other. do you think that because I have this one configured with an IP it will stop me getting another IP on another computer?

---

### Post by adster101 on 2007-12-03
Linuxonbute you were spot on!

As the other laptop I was using had already had an IP address assigned it looks like my ISP simply wouldn't assign me another IP for the other laptop.

Probably to test this I would do an ipconfig /release on the 'online' machine and then plug the cable into the other laptop.

I discovered that if I do a cold boot of the troubled laptop (with the modem already switched on) then the computer goes straight online.

Happy days.

Guess I need to look at sorting out a network now to share my IP address!

Thanks one and all. Now I can get on with figuring out the rest of this ubuntu thing!

:lolflag::lolflag:

---

