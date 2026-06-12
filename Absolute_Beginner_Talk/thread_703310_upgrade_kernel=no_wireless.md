---
title: "upgrade kernel=no wireless"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by gpmartinson on 2008-02-21
My system is great, but an update to a new version of the kernel made my wireless interface dissapear.  How do I go about figuring out how to diagnose and fix the problem.

---

### Post by jan quark on 2008-02-21
what is your wlan card?
did only the nm-applet disappear or the whole interface?

please run these terminal commands to clarify your current network status

```
lspci
```

```
sudo lshw -C network
```

```
iwconfig
```
```

ifconfig
```
```

sudo iwlist scan
```

```
cat /etc/network/interfaces
```

---

### Post by gpmartinson on 2008-02-21
lspci=
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
=======================
lshw=
      description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:1d:ab:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=10.103.3.63 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
iwconfig= 
blank
ifconfig=
eth0      Link encap:Ethernet  HWaddr 00:15:C5:1D:AB:FF  
          inet addr:10.103.3.63  Bcast:10.103.255.255  Mask:255.255.0.0
          inet6 addr: fe80::215:c5ff:fe1d:abff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5598317 (5.3 MB)  TX bytes:252722 (246.7 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
sudo iwlist scan =
blank
cat /etc/network/interfaces =

auto lo
iface lo inet loopback

Thanks, Gregg

---

### Post by mbsullivan on 2008-02-21
Hi Greg,

It looks to me like you've got an  Intel® PRO/Wireless 3945ABG. Assuming you used the standard Ubuntu kernel in the repositories, I believe all you have to do is download the latest iwlwifi driver from [http://intellinuxwireless.org/](http://intellinuxwireless.org/). [This]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz") snapshot should be fine.

After you get the tarball, untar it:

```
tar -xzf iwlwifi-1.2.25.tgz
```

Go to the proper directory:

```
cd iwlwifi-1.2.25
```

Make and install it (extra commands are for logging any errors that occur):

```
make 2>&1 | tee make.log
sudo make install 2>&1 | tee install.log
```

And then run the "load" script to load the correct kernel modules:

```
sudo ./load
```

Afterwards, your interface should be available and you should be able to connect to your wireless network. More information about discovering what interfaces are available and connecting to the network from the command line (for easy debugging on the forums) can be found [here]("http://ubuntuforums.org/showthread.php?t=698197").

If you have any problems, let me know. There are several other packages that used to be required from intelwireless.org, but hopefully they should no longer be an issue.

Mike

---

