---
title: "Internet Connection // Terminal Issues"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by _visible on 2006-03-18
**Helloes** to all of you willing to dedicate their time to this thread. 

Right during the installation process DHCP autoconfiguration failed. I have my network device (eth0) connected physically to a D-Link DI-604 (192.168.1.1) router. The DHCP is enabled on the router and the IP it is configured to assign to this machine's (hostname: ruckus) MAC address is 192.168.1.111.

I have no connection to the outside world on my Ubuntu installation as of right now. The network configuration panel in Administrative options is little help. "eth0" is activated and set as the default gateway device.

I've done a few things like ping 127.0.0.1. The loopback is successful. 

I've tried pinging my router at 192.168.1.1 and the destination host could not be reached. 

By using the network tools I've found out that my eth0 is indeed acquiring the IP properly (192.168.1.111), yet statistics say that packet are only being received and none are going to to the router. 

Disabled IPv6.



Please help! Thanks

---

### Post by Pragmatist on 2006-03-20
What is the output of these commmands:
```
ifconfig
```
```
dhclient eth0
```
```
netstat -i
```
```
route
```

You might try this:
```
route add default gw your_gateway_address
```
replacing your_gateway_address with, um, your gateway address :)

---

### Post by _visible on 2006-03-20
Ahh, thank you. I was getting pretty depressed. Performing the above right away and reporting back. 

I had this in my post above earlier, but I tried moderating some onfo out of it, since it was way long:

I am using Ubuntu 5.10 Breezy Badger x64

EDIT:

ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:13:8F:4F:96:03
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26959 (26.3 KiB)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35818 (34.9 KiB)  TX bytes:35818 (34.9 KiB)
```

dhclient eth0```

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:13:8f:4f:96:03
Sending on   LPF/eth0/00:13:8f:4f:96:03
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
Trying recorded lease 192.168.1.111
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

netstat -i```

Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0       172      0      0      0        0      0      0      0 BMU
lo    16436 0      1241      0      0      0     1241      0      0      0 LRU
```

route```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

route add default gw 192.168.1.1```

SIOCADDRT: Network is unreachable.
```

NOTE: Whenever I boot up, "Initiating Hotplug Subsystem" does not echo back an "ok". There is nothing in that field. "Configuring Network Interfaces" takes a really long time and finally synchronizing the clock echoes back a red "failed".

---

### Post by Princey on 2006-03-20
Are you sure that the ip address of the DLink is 192.168.1.1? I have a slighly lower module and the ip address is 192.168.0.1 In fact, as far as I know, most DLink routers if not all uses 192.168.0.1 as the default gateway. Give it a try and see what happens.

---

### Post by Pragmatist on 2006-03-20
> eth0      Link encap:Ethernet  HWaddr 00:13:8F:4F:96:03
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26959 (26.3 KiB)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe800

Your missing a line that looks like this:
> inet addr:192.168.xxx.xx  Bcast:255.255.255.255 Mask:255.255.255.0 but replace xxx.xx with your own address numbers :)

Here is an example of how you do it:
Using address 192.168.29.39  and netmask 255.255.255.0

```
ifconfig eth0 up 192.168.29.39 netmask 255.255.255.0
```

Then you configure your router (you use your gateway address, though):
```
route add default gw 192.168.29.1
```

Now try ```
ifconfig eth0
``` again and see what you get.  Let us know what happens.

---

### Post by _visible on 2006-03-20
[QUOTE=Princey]Are you sure that the ip address of the DLink is 192.168.1.1? I have a slighly lower module and the ip address is 192.168.0.1 In fact, as far as I know, most DLink routers if not all uses 192.168.0.1 as the default gateway. Give it a try and see what happens.[/QUOTE]
The router came default set at 192.168.0.1. I modified this, so rest assured, the default gateway is at 192.168.1.1. 


[QUOTE=Pragmatist]Your missing a line that looks like this:
[/QUOTE]Yes, I realize that. 

[QUOTE=Pragmatist]Here is an example of how you do it:
Using address 192.168.29.39  and netmask 255.255.255.0[/QUOTE]Wouldn't this be setting my ethernet device to a static ip? I'd like for it function under the DHCP mode.

---

### Post by Pragmatist on 2006-03-20
I think the command you want is **dhclient**  you can read about it with:
```
man dhclient
```
And find more man pages about dhcp like this:
```
man -k dhcp
```

And, this might also help:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by _visible on 2006-03-20
[QUOTE=Pragmatist]I think the command you want is **dhclient**  you can read about it with:
```
man dhclient
```
And find more man pages about dhcp like this:
```
man -k dhcp
```

And, this might also help:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)[/QUOTE]
Thanks. That link is looking great.

EDIT: According to the guide, the driver for my ethernet device is not loaded. It is:

lspci | grep Eth
```
0000:00:11.0 Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40)
```

EDIT2: I found the driver for my device. How can I install it? (i think i will try to help myself here by searching) This driver states it is for Kernel 2.6.x. I know Breezy Badger is 2.6.x; however, my installation is AMD64, will this affect anything?

EDIT3: With the driver were the installation instructions:

```
3.Installation Guide
====================
To install the driver, you should reconfigure and recompile your Linux 
kernel as follows:

Make sure your kernel version number is 2.6.x.

Copy uli526x.c to /usr/src/linux-2.6.x/drivers/net/tulip/, and modify the
following file in this directory. (Make a backup of them.)

1.Kconfig.in
add the following lines to Kconfig.in file.(refer to the Kconfig.in file we provide to you)

config ULI526X
	tristate "ULi M526x controller support"
	depends on NET_TULIP && PCI
	select CRC32
	---help---
	  This driver is for ULi M5261/M5263 10/100M Ethernet Controller
	  (<http://www.uli.com.tw/>).

	  To compile this driver as a module, choose M here.

2.Makefile
add the following lines to Makefile.(refer to the Makefile we provide to you)

obj-$(CONFIG_ULI526X)	+= uli526x.o
------------------------------------
Install as a kernel module
------------------------------------

  Step 1: 
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as module.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "m"

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make modules
	make modules_install

  Step 4:
	rmmod tulip
        modprobe uli526x	

 Then, you can bind any protocol into M5263 driver and use it.

------------------------------------------
Install as a part of linux kernel
------------------------------------------

  Step 1:
        Change directory to /usr/src/linux-2.6.x
        Use the command "make menuconfig" or "make xconfig", and make 
        sure "ULi M526x controller support" is set as kernel.
	
	Example:	
	Select "Device Drivers"
        Select "Networking support"
        Select "Ethernet (10 or 100Mbit)"
	Select "Tulip family network device support"
	Unselect "DECchip Tulip (dc2114x) PCI support"
        Select "ULi M526x controller support" as "y"
	

  Step 2:
        Select "Loadable module support", and unselect "Set version information
        on all module symbols"
	
	Before exit, save your configration.


  Step 3:
	make
	cp arch/i386/boot/bzImage /boot

  Step 4:
	If you use grub to boot your linux, then
	  1) Modify the file /etc/grub.conf by adding
		title 2.6.x
		root (hd0,2)
		kernel /boot/bzImage ro root=/dev/hd1
		The disk partition where your linux resides in, 
                for example: /dev/hda1
	  2) Reboot and select the kernel 2.6.x 
  
 Then, you can bind any protocol into M5263 driver and use it.
```

Do I have a choice between installing it as a kernel module or a part of the kernel, or do I have to do both the guides?

```
Change directory to /usr/src/linux-2.6.x
        Use the command "**make menuconfig**" or "**make xconfig**", and make 
        sure "ULi M526x controller support" is set as module.
```When i try to do this in terminal, bash says it cannot recognize the command.

Im totally lost.

---

### Post by _visible on 2006-03-25
[bump] Anyone?

---

### Post by thomas.hood on 2006-03-29
This is an apparently common problem, to which no-one on this forum seems to know the answer...

[http://ubuntuforums.org/showthread.php?t=146936&highlight=dhcpoffers](http://ubuntuforums.org/showthread.php?t=146936&highlight=dhcpoffers)

If you figure it let me know ](*,) 

Tom

---

### Post by Pragmatist on 2006-03-29
>  Originally Posted by: **_visible**
```
 lspci | grep Eth
0000:00:11.0 Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40) 

``` 


Do you know what brand/model/chipset of your ethernet device?

I think we should know that before installing any driver.  Also, how do you know that this driver you found pertains to your equipment?  Which equipment? ethernet card? router?

You might want to leave the router out of it for now and try connecting the modem directly to the ethernet port.

---

### Post by steve.horsley on 2006-03-29
It's defeatist and lazy I know, but I might be inclined to buy a real cheapie Ethernet card. In fact I got one for my last PC for £7. It had a realtek 8139 (?) chipset and worked out of the box. Believe me, it's nice not to have to compile  install a driver every time you reinstall Linux.

---

### Post by _visible on 2006-03-30
[QUOTE=steve.horsley]It's defeatist and lazy I know, but I might be inclined to buy a real cheapie Ethernet card. In fact I got one for my last PC for £7. It had a realtek 8139 (?) chipset and worked out of the box. Believe me, it's nice not to have to compile  install a driver every time you reinstall Linux.[/QUOTE]
Seems my ethernet device is NOT supported by Ubuntu 5.10 [now this is official]. I am not the only one with the issue, previous people remedied it by purchasing another ethernet card. I cannot afford to do this as both my PCI slots are taken up by a sound card as well as an analog video capture card. 

I have a hybrid motherboard you see: it has an AGP 8X and a PCI-E slow, 2PCI slots and a PCI-E x4 slot. But I do have NICs lying around, ironically. 

> Do you know what brand/model/chipset of your ethernet device?

I think we should know that before installing any driver. Also, how do you know that this driver you found pertains to your equipment? Which equipment? ethernet card? router?

You might want to leave the router out of it for now and try connecting the modem directly to the ethernet port.Absolutely. This was initially in my 1st post although I later removed it: I was afraid the length of the post would keep people from trying to help. 

I have an ASRock 939Dual-SATA2 motherboard with a built in Uli [Ali] Fast Ethernet Device. 

Northbridge: ULi M1695
Southbridge: ULI M1567

The following is an excerpt from the installation instructions:
> You can use command
        /sbin/lspci -n 
    or
        cat /proc/pci | grep 5263
to determine whether ULi **M5263** Ethernet controller exists in your 
system. If yes, simply follow the steps below to install the driver.

This driver is dedicated to support ULi M5263 10/100M Ethernet 
Controller under Linux platform.As you can see from my previous posts, I know this device exists in my system. Furthermore, this driver package was acquired directly from the chipset's manufacturer's website.

---

### Post by Pragmatist on 2006-03-30
So exactly what happens when you try to install the manufacturers drivers?

---

### Post by _visible on 2006-03-30
[QUOTE=Pragmatist]So exactly what happens when you try to install the manufacturers drivers?[/QUOTE]
Nothing. I can't install it period. I try to follow the directions until I come across a directory that doesn't exist or something i cannot quite execute.

---

### Post by Pragmatist on 2006-03-31
Please be specific. Paste the directions here and walk us through each step.  If you can't proceed past step one, what error messages do you get?  Even if you don't even get that far, please give us the full set of directions here.  If they are very long, include them in an attachment.

---

