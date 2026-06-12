---
title: "Wireless troubles"
date: 2007-06-21
forum: Apple PPC Users
---

### Post by stylecramper on 2007-06-21
I've got 7.04 on a G5 with Airport Extreme card, and a Netgear MR814v2. I've worked through all the wiki docs and threads on this topic. My airport card seems to be working, but it can't seem to see any wireless networks, including mine (everything works great in OS X). Any hints would be appreciated.

---

### Post by tcrroadie on 2007-06-23
Lets run a few commands to check your wireless card configuration.  Please post the output of these commands.  

Please post the output of lshw from "description: Wireless interface" till the beginning of "description: Ethernet interface"

```

sudo lshw -C network
```

```
ifconfig
```
```

iwconfig
```

And let us know what network you are trying to connect to from the list your receive from "iwlist".

```
sudo iwlist eth1 scan
```

Sorry for the late reply.

---

### Post by stylecramper on 2007-06-23
> **tcrroadie said:**
> Lets run a few commands to check your wireless card configuration.  Please post the output of these commands.  

Please post the output of lshw from "description: Wireless interface" till the beginning of "description: Ethernet interface"

```
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@05:01.0
       logical name: eth1
       version: 03
       serial: 00:0d:93:ea:86:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-powerpc64-smp latency=16 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:80704000-80705fff irq:57
```


> **tcrroadie said:**
> ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0D:93:2A:92:0E  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:93ff:fe2a:920e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048389 (1023.8 KiB)  TX bytes:50356 (49.1 KiB)
          Interrupt:41 Base address:0xf800 

eth1      Link encap:Ethernet  HWaddr 00:0D:93:EA:86:FF  
          inet6 addr: fe80::20d:93ff:feea:86ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:42 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:9120 (8.9 KiB)
          Interrupt:57 Base address:0x4000 

eth1:avah Link encap:Ethernet  HWaddr 00:0D:93:EA:86:FF  
          inet addr:169.254.11.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:57 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:346 (346.0 b)  TX bytes:346 (346.0 b)
```

> **tcrroadie said:**
> iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:9E:06:B4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
```


> **tcrroadie said:**
> And let us know what network you are trying to connect to from the list your receive from "iwlist".

```
eth1      Scan completed :
          Cell 01 - Address: F6:C0:00:01:00:16
                    ESSID:"" [192]
                    Protocol:?:&#65533;&#65533;IEEE 802.11b
Segmentation fault (core dumped)


```

I assume something's wrong with this list...my network's ESSID is backattheranch. Don't much like the look of that last line either.

> **tcrroadie said:**
> Sorry for the late reply.

No worries, much appreciated.

---

### Post by tcrroadie on 2007-06-23
Everything looks good except for the output you received from iwlist.  lets firts try running iwlist again.  There may be a minor bug in the bcm43xx driver causing the error. 

```
sudo iwlist eth1 scanning
```

If iwlist still bombs on you, lets next try reloading the bcm43xx driver module. In your terminal run each command one at a time. 

Bring down your wireless card. 

```
sudo ifdown eth1 
```

This will remove the bcm43xx driver module, disabling your wireless card. 
```
sudo modprobe -r bcm43xx
``` 

This will restart the Broadcom driver module and enable your wireless card.
```
sudo modprobe bcm43xx
```

Bring back up your wireless card.
```
sudo ifup eth1
```

Then run iwlist again.
```
sudo iwlist eth1 scanning
```

If iwlist is still causing you problems, post your information on your wireless network. 

essid 

channel 

encryption is used.

I would really rather see the output from iwlist though.

---

### Post by stylecramper on 2007-06-23
> **tcrroadie said:**
> Everything looks good except for the output you received from iwlist.  lets firts try running iwlist again.  There may be a minor bug in the bcm43xx driver causing the error. 

```
sudo iwlist eth1 scanning
```

There does seem to be a weird problem. I got the same output from iwlist about four times in a row, then I got this:

```
eth1      Scan completed :
          Cell 01 - Address: 00:00:00:01:00:16
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=86/100  Signal level=-73 dBm  Noise level=-60 dBm
                    Extra:
          Cell 02 - Address: 00:00:00:01:00:0C
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=95/100  Signal level=-52 dBm  Noise level=-64 dBm
                    Extra:
          Cell 03 - Address: 00:00:00:01:00:14
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=96/100  Signal level=-49 dBm  Noise level=-60 dBm
                    Extra:
          Cell 04 - Address: 00:00:00:01:00:09
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel=0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=91/100  Signal level=-62 dBm  Noise level=-60 dBm
                    Extra:
          Cell 05 - Address: 00:00:00:01:00:0F
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel=0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=86/100  Signal level=-73 dBm  Noise level=-60 dBm
                    Extra:
          Cell 06 - Address: 00:00:00:01:00:09
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel=0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=91/100  Signal level=-62 dBm  Noise level=-60 dBm
                    Extra:
```

But it's inconsistent.

> **tcrroadie said:**
> If iwlist still bombs on you, lets next try reloading the bcm43xx driver module. In your terminal run each command one at a time. 

Bring down your wireless card. 

```
sudo ifdown eth1 
```

This will remove the bcm43xx driver module, disabling your wireless card. 
```
sudo modprobe -r bcm43xx
``` 

This will restart the Broadcom driver module and enable your wireless card.
```
sudo modprobe bcm43xx
```

Bring back up your wireless card.
```
sudo ifup eth1
```

Then run iwlist again.
```
sudo iwlist eth1 scanning
```

The result of [COLOR="Blue"]sudo ifdown eth1[/COLOR] was:

```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 8008
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
```

> **tcrroadie said:**
> If iwlist is still causing you problems, post your information on your wireless network. 

essid 

channel 

encryption is used.

I would really rather see the output from iwlist though.

essid: backattheranch
channel: 11
encryption: WEP 128bit, Authentication Type: Automatic, 26-character key

---

### Post by stylecramper on 2007-06-23
Tried [COLOR="Blue"]sudo ifdown eth1 again[/COLOR]; result was

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by tcrroadie on 2007-06-23
> **stylecramper said:**
> Tried [COLOR="Blue"]sudo ifdown eth1 again[/COLOR]; result was

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

This is normal output for a network that is not properly configured.  

The purpose of the steps I posted, was to gracefully bring down your wireless network card and reload the Broadcom driver and bring your wireless card back up.  Did your run all of the previous commands that I posted in that order?  Did iwlist report properly afterwards. 

Moving on, you could try to set your network settings manually and see what happens.  

1.  First make sure that your wireless router/wap is configured for a mixed network.  B&G

2.  Disable your WEP encryption temporarily for testing, just to see if you can connect to an open network. 

3.  Make sure your router/wap is configured for DHCP.  

Lets set your wireless network settings.  We will be editing a file called interfaces. 

First bring down you wireless card.
```
sudo ifdown eth1
``` 

Next open the file interfaces in gedit, so we can set your network settings. 
```

sudo gedit /etc/network/interfaces
```

Add this to the bottom of this file.
```
auto eth1
iface eth1 inet dhcp
wireless-essid backattheranch
```

Save and close gedit. 

Now bring back up your wireless card. 

```
sudo ifup eth1
```

Please post the output received when you ran "sudo ifup eth1".  Hopefully you will get a network address from your router.  If you did, you can run ifconfig to double check. 

```
ifconfig
```

---

### Post by stylecramper on 2007-06-24
> **tcrroadie said:**
> This is normal output for a network that is not properly configured.  

The purpose of the steps I posted, was to gracefully bring down your wireless network card and reload the Broadcom driver and bring your wireless card back up.  Did your run all of the previous commands that I posted in that order?  Did iwlist report properly afterwards. 

I did run all the commands; iwlist reported as I stated above.

> **tcrroadie said:**
> Moving on, you could try to set your network settings manually and see what happens.  

1.  First make sure that your wireless router/wap is configured for a mixed network.  B&G

Netgear advertises it as an 802.11b router.

> **tcrroadie said:**
> 2.  Disable your WEP encryption temporarily for testing, just to see if you can connect to an open network. 

No, couldn't connect.

> **tcrroadie said:**
> 3.  Make sure your router/wap is configured for DHCP.  

Yes.

> **tcrroadie said:**
> Lets set your wireless network settings.  We will be editing a file called interfaces. 

First bring down you wireless card.
```
sudo ifdown eth1
``` 

Output was:[COLOR="Blue"] ifdown: interface eth1 not configured[/COLOR]

> **tcrroadie said:**
> Next open the file interfaces in gedit, so we can set your network settings. 
```

sudo gedit /etc/network/interfaces
```

Add this to the bottom of this file.
```
auto eth1
iface eth1 inet dhcp
wireless-essid backattheranch
```

Save and close gedit. 

Those lines were already present.

> **tcrroadie said:**
> Now bring back up your wireless card. 

```
sudo ifup eth1
```

Please post the output received when you ran "sudo ifup eth1".  Hopefully you will get a network address from your router.  If you did, you can run ifconfig to double check. 

```
ifconfig
```

Result of [COLOR="Blue"]sudo ifup eth1[/COLOR]:

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Result of [COLOR="Blue"]ifconfig:[/COLOR]

```
eth0      Link encap:Ethernet  HWaddr 00:0D:93:2A:92:0E  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:93ff:fe2a:920e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:12547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11612255 (11.0 MiB)  TX bytes:1189404 (1.1 MiB)
          Interrupt:41 Base address:0xf800 

eth1      Link encap:Ethernet  HWaddr 00:0D:93:EA:86:FF  
          inet6 addr: fe80::20d:93ff:feea:86ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1357 errors:0 dropped:4331 overruns:0 frame:0
          TX packets:1003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:631624 (616.8 KiB)  TX bytes:257951 (251.9 KiB)
          Interrupt:57 Base address:0x9000 

eth1:avah Link encap:Ethernet  HWaddr 00:0D:93:EA:86:FF  
          inet addr:169.254.11.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:57 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4200 (4.1 KiB)  TX bytes:4200 (4.1 KiB)
```

---

### Post by stylecramper on 2007-06-24
Tried [COLOR="Blue"]sudo ifdown eth1[/COLOR] a second time; output was:

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 2994
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
```

Output of [COLOR="Blue"]sudo ifup eth1[/COLOR] was:

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by tcrroadie on 2007-06-24
Ok.  First, the output you posted from "ifconfig' looks as if you have an ethernet cable connected to your pc.  eth0 reports an ip address. 

```
eth0      Link encap:Ethernet  HWaddr 00:0D:93:2A:92:0E  
          [COLOR="Red"]inet addr:192.168.0.4[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:93ff:fe2a:920e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:12547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          [COLOR="Red"]RX bytes:11612255 (11.0 MiB)  TX bytes:1189404 (1.1 MiB)[/COLOR]
          Interrupt:41 Base address:0xf800 
```

When I asked if you could temporarily disable your WEP encryption, you said you couldn't connect.  Could you possibly connect to your router using your wired ethernet connection, or OSX to disable your encryption?

Some users have reported that there wireless network cards do not operate properly when there is an ethernet cable connected to their pc's.  Lets disconnect your wired connection from here on out and see what happens. 

Moving on again.  Obviously if your router has WEP enabled and has a key set, we will need to add your WEP key to the /etc/network/interfaces file.  

Bring down your wirless device again (eth1)

```
sudo ifdown eth1
```

Open up the interfaces file again in gedit, and add "wireless-key yourkeyhere" to the eth1 section of the file.  Replace yourkeyhere with the actual WEP key set on your router, not the passphrase.  Should look something like this. 

```
auto eth1
iface eth1 inet dhcp
wireless-essid backattheranch
wireless-key yourkeyhere
```

Save and close the file.

Now lets bring your wireless card back up again.

```
sudo ifup eth1
```

If you still are not receiving an ip address for eth1, try restarting your network. 
```
sudo /etc/init.d/networking restart
```

Run iwlist again with your ethernet cable disconnected.

```
sudo iwlist eth1 scanning
```

---

### Post by stylecramper on 2007-06-25
> **tcrroadie said:**
> Ok.  First, the output you posted from "ifconfig' looks as if you have an ethernet cable connected to your pc.  eth0 reports an ip address. 

```
eth0      Link encap:Ethernet  HWaddr 00:0D:93:2A:92:0E  
          [COLOR="Red"]inet addr:192.168.0.4[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:93ff:fe2a:920e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:12547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          [COLOR="Red"]RX bytes:11612255 (11.0 MiB)  TX bytes:1189404 (1.1 MiB)[/COLOR]
          Interrupt:41 Base address:0xf800 
```

When I asked if you could temporarily disable your WEP encryption, you said you couldn't connect.  Could you possibly connect to your router using your wired ethernet connection, or OSX to disable your encryption?

Some users have reported that there wireless network cards do not operate properly when there is an ethernet cable connected to their pc's.  Lets disconnect your wired connection from here on out and see what happens. 

Sorry for the confusion. I do have an Ethernet cable connected to the router; that's how I've been reading and posting to this forum. What I meant was, after disabling my WEP encryption through the Ethernet cable, then disconnecting the cable, I couldn't connect wirelessly.

> **tcrroadie said:**
> Moving on again.  Obviously if your router has WEP enabled and has a key set, we will need to add your WEP key to the /etc/network/interfaces file.  

Bring down your wirless device again (eth1)

```
sudo ifdown eth1
```

Open up the interfaces file again in gedit, and add "wireless-key yourkeyhere" to the eth1 section of the file.  Replace yourkeyhere with the actual WEP key set on your router, not the passphrase.  Should look something like this. 

```
auto eth1
iface eth1 inet dhcp
wireless-essid backattheranch
wireless-key yourkeyhere
```

Save and close the file.

Now lets bring your wireless card back up again.

```
sudo ifup eth1
```

OK, did all that. Result of [COLOR="Blue"]sudo ifup eth1[/COLOR] was:

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0d:93:ea:86:ff
Sending on   LPF/eth1/00:0d:93:ea:86:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


> **tcrroadie said:**
> If you still are not receiving an ip address for eth1, try restarting your network. 
```
sudo /etc/init.d/networking restart
```

Run iwlist again with your ethernet cable disconnected.

```
sudo iwlist eth1 scanning
```

Got this six times:

```
eth1      Scan completed :
          Cell 01 - Address: 00:00:00:01:00:0C
                    ESSID:off/any/hidden
                    Protocol:
Segmentation fault (core dumped)
```

Then got this:

```
eth1      Scan completed :
          Cell 01 - Address: 00:00:00:01:00:0C
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=94/100  Signal level=-55 dBm  Noise level=-60 dBm
                    Extra:
          Cell 02 - Address: 00:00:00:01:00:0C
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=86/100  Signal level=-73 dBm  Noise level=-60 dBm
                    Extra:
          Cell 03 - Address: 00:00:00:01:00:14
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=96/100  Signal level=-50 dBm  Noise level=-60 dBm
                    Extra:
          Cell 04 - Address: 00:00:00:01:00:16
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel:0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                              0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=86/100  Signal level=-73 dBm  Noise level=-60 dBm
                    Extra:
          Cell 05 - Address: 00:00:00:01:00:09
                    ESSID:off/any/hidden
                    Protocol: 
                    Mode:Auto
                    Mode:Master
                    Channel=0
                    Encryption key:18
                    Bit Rates:0 kb/s; 0.05 kb/s; 0.05 kb/s; 0.05 kb/s
                    Quality:0  Signal level:0  Noise level:0
                    Quality=90/100  Signal level=-64 dBm  Noise level=-60 dBm
                    Extra:
```

---

### Post by tcrroadie on 2007-06-27
I'm starting to get the feeling that the Broadcom chipset used in your G5 Mac may not be fully supported yet.  The lack of wireless network information given from "iwlist" leads me to believe this.  I have never liked the output "iwlist" has given you.  

If you are really gung-hoe about trying to get your wireless card working you can visit the IRC chat channel for the bcm43xx driver.  You can possibly try to give them some more information on the version of the Broadcom 4306 chip used in your G5 mac and note the lack of information given by "iwlist". 

> Official (english) user IRC channel: irc.freenode.net #bcm-users

You can also visit these web sites for the bcm43xx driver to find out more information. 

[Home - Broadcom 43xx]("http://bcm43xx.berlios.de/")

[Linux Wireless - bcm43xx]("http://linuxwireless.org/en/users/Drivers/bcm43xx#head-0af89c119bcf2e61329f5a324647ccb232676d76")

Sorry I couldn't help out some more on this.  :(

---

