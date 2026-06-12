---
title: "no wireless networks"
date: 2012-01-17
forum: Any Other OS
---

### Post by madhan4u on 2012-01-17
Hi, I have installed Backtrack 5r1 on myDELL inspiron 15R. wired  connetion is working perfectly, but the only problem is with wireless. please find the below usefl info:

root@bt:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
-------------------------------------------------------
# cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory
-------------------------------------------------------
# dmesg | grep -e eth0 -e bcm
[    3.661882] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc9000067c000, f0:4d:a2:ba:0e:1b, XID 04e00000 IRQ 41
[    9.960182] r8169 0000:13:00.0: eth0: link down
[    9.960203] r8169 0000:13:00.0: eth0: link down
[    9.960589] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.776699] r8169 0000:13:00.0: eth0: link up
[   11.777077] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.631339] eth0: no IPv6 routers present
---------------------------------------------------------------

lshw -C Network
  *-network UNCLAIMED                                                                                                                                                                           
       description: Network controller                                                                                                                                                          
       product: BCM4313 802.11b/g/n Wireless LAN Controller                                                                                                                                     
       vendor: Broadcom Corporation                                                                                                                                                             
       physical id: 0                                                                                                                                                                           
       bus info: pci@0000:12:00.0                                                                                                                                                               
       version: 01                                                                                                                                                                              
       width: 64 bits                                                                                                                                                                           
       clock: 33MHz                                                                                                                                                                             
       capabilities: pm msi pciexpress bus_master cap_list                                                                                                                                      
       configuration: latency=0                                                                                                                                                                 
       resources: memory:fbd00000-fbd03fff                                                                                                                                                      
  *-network                                                                                                                                                                                     
       description: Ethernet interface                                                                                                                                                          
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller                                                                                                                          
       vendor: Realtek Semiconductor Co., Ltd.                                                                                                                                                  
       physical id: 0                                                                                                                                                                           
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:ba:0e:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=124.123.8.16 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:41 ioport:d000(size=256) memory:d0c10000-d0c10fff memory:d0c00000-d0c0ffff memory:fb300000-fb31ffff
-------------------------------------------------------------
# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
---------------------------------------------------------------------------
# sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with 'ndiswrapper'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with 'ndiswrapper'
FATAL: Module wl not found.
FATAL: Error running install command for wl
-----------------------------------------------------------------------------
# dmesg | grep -e wl -ie firmware -e wlan -ie radio
[    0.838080] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.866438] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
----------------------------------------------------------------------------
modinfo wl
ERROR: modinfo: could not find module wl
---------------------------------------------------------------------------
I tried all the possible ways mentioned in the forum. but no use..
I tried to execute
sudo apt-get purge bcmwl-kernel-source, but getting error::
Error! Bad return status for module build on kernel: 2.6.39.4 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.39.4
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


my Network controller is: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01).

please help me..

---

### Post by pytheas22 on 2012-01-18
If you're using Backtrack, you would probably find better help on a Backtrack forum.  I haven't used that distribution in a long time.  You need the 'wl' driver to support your device (b43 says it is untested, according to its [webpage]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices")) and I have no idea whether Backtrack has an easy way to install that driver via the package manager, like Ubuntu does.  If it does not, you will need to download the source code from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and compile it yourself.

---

### Post by nothingspecial on 2012-01-18
Moved to Other OS/Distro Talk.

---

### Post by madhan4u on 2012-01-18
Thanks for the reply. 
I have been trying to solve this issue for couple of days. But I couldnot bring up wireless device. Wlan0 is not displaying in ifconfig. And not able to solve wl module driver issue.. Don't know how to solve. If you can traceout any problem, please let me know. 
Thanks

---

### Post by pytheas22 on 2012-01-19
The problem is that the wl module is not installed on your system, as indicated by the error messages you received when you typed "sudo modprobe wl"  Without the wl module no wireless interface will exist in ifconfig.

The solution is simply to install the wl module.  On Ubuntu you can do that easily by installing the "bcmwl-kernel-source" package.  However, you're using Backtrack, which is a different operating system.  I have no idea whether Backtrack has a similar package for installing the wl module, and if so what it is called.  You can try searching the package manager (I'm not sure which one Backtrack uses; probably Synaptic) for a package that mentions "bcmwl," "STA" or "wl," or just google to figure it out.

Otherwise, if there's no package available for installing the wl driver, you will need to compile it from source.  The source code, as I've said, is available at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  The README file there provides instructions on building and installing the driver from source.

---

### Post by imachavel on 2012-01-19
well wait wait wait

despite that wireless module he is using. What if it's hardware? Why don't you try removing the wireless adapter and then try testing it in another lap top? or try a different duplicate wireless adapter and swap it and test it in your lap top. Sorry I'm not good with ls read outs seeing your hard ware and installed drivers. If your hard wired network connection is working, then why would it be a driver issue? Ok a lap top has a separate wireless adapter driver, that's true. But I don't know. Could be wireless adapter, could be back track, but does back track module work with only hard wired and not wireless?

you sure know your software, but also, CHECK CHECK CHECK and TEST the hardware, I would ask you to use a web cam, and take a picture of your wireless lap top switch so we could all see if it's for sure on or not, but nobody here is going to treat you like your stupid like people do on other forums. I've seen wireless laptop problems, and it's hardly ever a software issue, especially if things work hard wired.

---

### Post by imachavel on 2012-01-19
sudo modprobe wl
[sudo] password for danel: 
FATAL: Module wl not found.

that sure is true, I have no wireless adapter installed next to main board(I'm not using a latop) so command can't possibly work for me :popcorn:

---

### Post by pytheas22 on 2012-01-19
> **imachavel said:**
> well wait wait wait

despite that wireless module he is using. What if it's hardware? Why don't you try removing the wireless adapter and then try testing it in another lap top? or try a different duplicate wireless adapter and swap it and test it in your lap top. Sorry I'm not good with ls read outs seeing your hard ware and installed drivers. If your hard wired network connection is working, then why would it be a driver issue? Ok a lap top has a separate wireless adapter driver, that's true. But I don't know. Could be wireless adapter, could be back track, but does back track module work with only hard wired and not wireless?

you sure know your software, but also, CHECK CHECK CHECK and TEST the hardware, I would ask you to use a web cam, and take a picture of your wireless lap top switch so we could all see if it's for sure on or not, but nobody here is going to treat you like your stupid like people do on other forums. I've seen wireless laptop problems, and it's hardly ever a software issue, especially if things work hard wired.

Thanks for your suggestions, but it's definitely not the hardware.  The hardware exists and is detected, as indicated by this line in the "lspci -nn" output:
```

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

Nor is it a question of the wireless being switched on or off.  Those switches disable the radio in the wireless card; they don't disable the hardware itself.

The problem is clear and simple: the original poster just needs to install the 'wl' driver.  Unfortunately I just don't know exactly how to do that in Backtrack.

---

