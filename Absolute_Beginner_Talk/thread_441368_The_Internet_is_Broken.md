---
title: "The Internet is Broken"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-05-12
I recently installed Ubuntu 7.04 on my Compaq Presario V2000 laptop and it has been mostly working fine.  However, I have not been able to connect to the internet via wired or wireless connections.  I am only concerned with the wireless connection because that is all I use.  Ubuntu shows this connection as working, but it is in fact, not.  After reading around the forums a bit I realised that it was probably because the hardware is not recongnized.  I then got driverloader (driverloader_2.37_k2.6.20_15_generic_ubuntu_i386.deb) from Linuxart and the driver (sp31172.exe) for my Intell Pro/wireless card from the Compaq website.  I moved them into Ubuntu via a CD and a flash drive.  I tried to install the driverloader package using the command 'dpkg -i', but whenever I do this I get the message:

dpkg: error processing driverloader_2.37_k2.6.20_15_generic_ubuntu_i386.deb (--install):
        cannot access archive: No such file or directory
Errors were encountered whle processing:
        driverloader_2.37_k2.6.20_15_generic_ubuntu_i386.deb

If anyone knows what is wrong or what I am doing wrong please let me know.

Thanks in advance, Greg.

---

### Post by foresth on 2007-05-12
It seems you miswrote the "driverloader_2.37_k2.6.20_15_generic_ubuntu_i386.d eb". There is a space in "d eb", you see? So the error is that there is no such file.

Btw, you can use eg. dpkg -i driverloader_*.deb
.

---

### Post by Najand on 2007-05-12
Send us the output of "ifconfig" command.

---

### Post by annda on 2007-05-12
you have a typo (extra space)

driverloader_2.37_k2.6.20_15_generic_ubuntu_i386.**d eb**

also, intel wireless is supported by ubuntu. you should install the restricted kernel modules - check the restricted driver manager under system>administration

---

### Post by GregoryMA on 2007-05-12
Here is the output of ifconfig:

eth0     Link encap:Ethernet HWaddr 00:C0:9F:B5:29:A3
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
       Interrupt:19 Base address:0xc000

eth0:avah Link encap:Ethernet HWaddr 00:C0:9F:B5:29:A3
       inet addr:169.254.7.241 Bcast:169.254.255.255 Mask:255.255.0.0
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       Interrupt:19 Base address:0xc000

lo    Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:34 errors:0 dropped:0 overruns:0 frame:0
       TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:2564 (2.5 KiB) TX bytes:2564 (2.5 KiB)\

I checked the restricted driver manager but there was only one driver there.  It was an ATI driver for the graphics card.  Is there supposed to be a driver there for the wireless card too?

I did not copy the driver name or error message into my original question so the typo was just in the message and not in my commands.  

So I shouldn't be even trying to install this program since Intel is supported by Ubuntu, right?

---

### Post by annda on 2007-05-12
can you give us the list of your network devices by running this command:
```

sudo lshw -C network
```

you probably don't need extra programs. check synaptic to see if you have the restricted kernel modules installed for your kernel (tip: search for 'linux' in name)

---

### Post by GregoryMA on 2007-05-13
Here is the list of my network devices:

*network:0
      description: Ethernet interface
      product: RTL8139/
      8139C/8139C+
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: 0
      bus info: pci@05:00.0
      logical name: eth0
      version: 10
      serial: 00:c0:9f:b5:29:a3
      size: 10MB/s
      capacity: 100MB/s
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical tp mii 10bt 10btfd
      100bt 100btfd
      autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half
latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
      resources: ioport:a000a0ff iomemory:d0208000d02080ff irq:19
*network:1 DISABLED
      description: Wireless interface
      product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
      vendor: Broadcom Corporation
      physical id: 2
      bus info: pci@05:02.0
      logical name: eth1
      version: 02
      serial: 00:90:4b:f9:2a:ec
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master ethernet physical wireless
      configuration: broadcast=yes driver=bcm43xx driverversion=2.6.2015generic
      latency=64 link=no
multicast=yes wireless=IEEE 802.11b/g
      resources: iomemory:d0204000d0205fff irq:20

I found three restricted kernel modules in Synaptic:

linux-restricted-modules-generic      2.6.20.15.14
linux-restricted-modules-common     2.6.20.5-15.20
linux-restricted-modules-2.6.20-25-generic     2.6.20.5-15.20

---

### Post by annda on 2007-05-13
oops, you don't have intel wireless, but broadcom. it is officially not linux-friendly. you seem to have a kernel module as a driver but from what i read it does not work well.

i'm sorry but i can't help you here. please search the forums and user documentation [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
for broadcom.

---

