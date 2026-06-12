---
title: "Wi-Fi Not Working"
date: 2011-06-24
forum: Apple Hardware Users
---

### Post by Dorian72 on 2011-06-24
I have an iMac (the model identifier is 4,1). It's one of the white ones and it has ATI Radeon X1600 graphics. I can't get the wi-fi to work in Ubuntu. It doesn't detect any networks (Mac OS X usually detects 3 or 4 from around the neighborhood). I tried installing the wireless driver from the "Additional Drivers" Application, but it still doesn't detect any networks. My network has a WPA key, but it's not even detecting my neighbors' open networks. This is the first time I've used Ubuntu, and I've searched Google many, many times. Any help would be greatly appreciated. I did successfully get a connection when I moved my computer by the router and plugged in via Ethernet.

---

### Post by pauljwells on 2011-06-25
The community pages has this. Not sure how well NDISWrapper works these days

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

Before trying that though, have you run the additional driver search in system settings? It _should_ work out of the box...

---

### Post by Dorian72 on 2011-06-25
I downloaded the driver from "Additional Drivers" and activated it. It still doesn't work, though. None of the tutorials I've read for NDISwrapper have worked, but I haven't seen that one yet. It looks promising, I'll give it a shot. Thank you, I'll post my results. :)

---

### Post by varunendra on 2011-06-25
I'm not familiar with iMacs, but output of following commands should help anybody who can help:

```
sudo lshw -C network
```
```
iwconfig
```
and
```
ifconfig
```

Besides, which version of Ubuntu are you using? Did you try to update your system when you got connected via Ethernet cable?

---

### Post by Dorian72 on 2011-06-25
> **varunendra said:**
> I'm not familiar with iMacs, but output of following commands should help anybody who can help:

```
sudo lshw -C network
``````
iwconfig
```and
```
ifconfig
```Besides, which version of Ubuntu are you using? Did you try to update your system when you got connected via Ethernet cable?
I'm running Ubuntu 11.04, so there shouldn't be a need to update.

Could you please explain what each of those commands does? Thank you. :)

---

### Post by varunendra on 2011-06-25
I think you are confusing 'update' with 'upgrade'. These are different things.

In fact most often you need those updates more frequently when you use the latest release, since initial releases are often not much stable and full of bugs for which they regularly release fixes and patches. These updates also include new or updated driver modules. For 11.04, I'd suggest to update twice or maybe even thrice every week until you get everything working and stable!:)

Be informed though - these updates (for latest releases) may sometimes even break the system which might otherwise have been working somehow. That's why latest releases are recommended only for those who are enthusiastic and like to experiment! For those who like a stable system, only LTS and slightly old releases are recommended (like 10.04.2 LTS currently).

Command explanations:

**lshw** lists all your hardware with their essential details including drivers in use. With argument **-C network**, the output limits to only those hardware which are network related, i.e. lan and wireless adapters.

**ifconfig** produces network adapters' general configuration and some statistical details regarding network communication.

**iwconfig** is same as ifconfig, only it produces wireless related details.

All of these commands can do much more than what I explained, but when used with different arguments.

I asked their output as these will tell any potential troubleshooter about your hardware details, their essential configuration details and driver modules currently used by them.

Based on these details, you may be further asked to post some more outputs, or with any luck, a direct solution to implement.

---

### Post by Dorian72 on 2011-06-25
> **varunendra said:**
> I think you are confusing 'update' with 'upgrade'. These are different things.

In fact most often you need those updates more frequently when you use the latest release, since initial releases are often not much stable and full of bugs for which they regularly release fixes and patches. These updates also include new or updated driver modules. For 11.04, I'd suggest to update twice or maybe even thrice every week until you get everything working and stable!:)

Be informed though - these updates (for latest releases) may sometimes even break the system which might otherwise have been working somehow. That's why latest releases are recommended only for those who are enthusiastic and like to experiment! For those who like a stable system, only LTS and slightly old releases are recommended (like 10.04.2 LTS currently).

Command explanations:

**lshw** lists all your hardware with their essential details including drivers in use. With argument **-C network**, the output limits to only those hardware which are network related, i.e. lan and wireless adapters.

**ifconfig** produces network adapters' general configuration and some statistical details regarding network communication.

**iwconfig** is same as ifconfig, only it produces wireless related details.

All of these commands can do much more than what I explained, but when used with different arguments.

I asked their output as these will tell any potential troubleshooter about your hardware details, their essential configuration details and driver modules currently used by them.

Based on these details, you may be further asked to post some more outputs, or with any luck, a direct solution to implement.
I will plug my iMac back into the modem and run an update tomorrow, thank you for explaining that.

I'll also run those commands and post the results. Thank you so much for your help. :)

---

### Post by Dorian72 on 2011-06-26
> **varunendra said:**
> I'm not familiar with iMacs, but output of following commands should help anybody who can help:

```
sudo lshw -C network
``````
iwconfig
```and
```
ifconfig
```Besides, which version of Ubuntu are you using? Did you try to update your system when you got connected via Ethernet cable?
I ran an update and then ran the commands you suggested.

After running iwconfig:
```
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 22
       serial: 00:16:cb:83:c6:f1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:88200000-88203fff ioport:1000(size=256) memory:88500000-8851ffff
  *-network UNCLAIMED
       description: Network controller

```After running iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```After running ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:cb:83:c6:f1  
          inet addr:172.16.15.15  Bcast:172.16.15.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:fe83:c6f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173306272 (173.3 MB)  TX bytes:4452909 (4.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3488 (3.4 KB)  TX bytes:3488 (3.4 KB)

```Of course, I have no clue what any of that means. :p Any help would be much appreciated. :) I was plugged into the modem via Ethernet when I ran these commands, not sure if that affects the output or not.

---

### Post by varunendra on 2011-06-26
> **Dorian72 said:**
> 
```
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
....
....
  *-network UNCLAIMED
       description: Network controller

```
Apparently, your wifi adapter was perhaps powered off while running these commands. Is there an on/off switch for it? I've also seen some laptops having a BIOS feature to automatically turn off the Wifi when it is connected to Ethernet, but can't say what's the case with an iMac.

If there is any on/off switch for wifi, turn it on then run the commands. If not, try them after disconnecting from ethernet (cable connection) and rebooting to see if it makes any difference in the output. The 'UNCLAIMED' adapter in your first output maybe the wifi adapter, but I'm confused with this kind of output.

In the next two outputs, there must be entries regarding wlan0 or pan0 or something alike (just as there are for eth0).

Your current outputs hint as if your wifi adapter is not even detected by the kernel. I'm afraid if that is the case, then fiddling with different drivers is not going to be of any use. But the presence of an 'UNCLAIMED' adapter gives some hope - only if we can get some more details about it.

---

### Post by Dorian72 on 2011-06-26
I've gotten the wi-fi to work with Puppy Linux before. This is the first time I've actually installed a Linux distro to my iMac. But I would assume that if the wi-fi worked with Puppy, it would work with Ubuntu. Am I correct? I'll reboot into Ubuntu and run those commands again. Thanks again. :)

---

### Post by varunendra on 2011-06-26
> **Dorian72 said:**
> I would assume that if the wi-fi worked with Puppy, it would work with Ubuntu.
It 'should', but that depends upon kernel version + driver in use.

---

