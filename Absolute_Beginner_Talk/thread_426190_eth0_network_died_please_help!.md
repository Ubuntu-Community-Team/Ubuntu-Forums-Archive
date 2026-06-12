---
title: "eth0 network died? please help!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by darkdays on 2007-04-28
I've been running Feisty for about a week, fixing a lot of small issues along the way.
But this just makes me wonder what the hell has happened. Ethernet connection has been working flawless all along, not much meddling with it at all. I'm running static ip on ethernet to my uni-network, so no wireless, dsl or anything. 
As far as I know I haven't touched anything near the networkconfig today, but after returning from the supermarket my connection was gone. First thought it might be a network problem, so I went about with some non-computer stuff. Rebooted, and now Feisty complained about eth0 not existing. "sudo ifconfig eth0 up" gave something like; "Device does not exist" and in the lspci I couldn't find my eth-controller at all.

Fired up Vista for the first time since installing Feisty just to check, no problems at all here.

Tried booting Feisty again, now it found eth0 but no network access. So I looked around and the output of ifconfig, route -n & lspci is at the bottom of this post. 

Writing this from Vista now and no problems at all with the network :confused: 

```
ifconfig:

eth0      
Link encap:Ethernet  HWaddr 00:13:8F:C4:26:0E     
inet addr:193.11.219.22  Bcast:193.11.219.255  Mask:255.255.254.0          
inet6 addr: 2002:c10b:da43:4:213:8fff:fec4:260e/64 Scope:Global          
inet6 addr: fec0::4:213:8fff:fec4:260e/64 Scope:Site          
inet6 addr: fe80::213:8fff:fec4:260e/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:655 errors:0 dropped:4294967274 overruns:0 frame:0          
TX packets:153 errors:0 dropped:46 overruns:0 carrier:0        
collisions:0 txqueuelen:1000           
RX bytes:81475 (79.5 KiB)  TX bytes:13519 (13.2 KiB)          
Interrupt:17 Base address:0xc000 


route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
193.11.218.0    0.0.0.0         255.255.254.0   U     0      0        0 eth


lspci:

001:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

---

### Post by lloyd_b on 2007-04-28
> route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
193.11.218.0    0.0.0.0         255.255.254.0   U     0      0        0 eth

There's no gateway defined, so you won't be able to access anything outside of the local network.

If you know what your gateway should be:
```
sudo route add default gw {IP Address} eth0
```
in a terminal window, and see if that restores your internet connection.

You mentioned that you have static IP - could you post the contents of the file "/etc/network/interfaces"?  This is where the problem probably is.

Lloyd B.

---

### Post by darkdays on 2007-04-28
Strangely when I booted to do the changes everything was back to normal again, network working like nothing happened. 

Now route -n gives:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
193.11.218.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         193.11.218.1    0.0.0.0         UG    0      0        0 eth0
```

and cat /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 193.11.219.22
netmask 255.255.254.0
gateway 193.11.218.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

What could have caused it?

---

### Post by lloyd_b on 2007-04-29
>  Strangely when I booted to do the changes everything was back to normal again, network working like nothing happened.
> 
What could have caused it?

Sunspots, Gremlins, an intermittent problem with the ethernet card, take your pick.  As a rule, problems like this are *extremely* difficult to diagnose.

Lloyd B.

---

### Post by darkdays on 2007-04-29
Damn, happened again today after one of those freezes where the cursor still responds to the mouse and apps seem to keep working but the whole gui is completely unresponsive, although that's another issue. Had to force a reboot and coming back it's like the onboard eth-card isn't even there. Another reboot and voila, everything back to normal. Tried checking the logs but can't find anything that was utterly strange, although I'm not sure which log I'm supposed to check and for what.

```
petter@gaia:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

petter@gaia:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
```

After the reboot, with Ethernet controller up and running again:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
**01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)**
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
```

---

### Post by TheOtherShoe on 2007-05-04
I have the same ethernet card, according to lspci, and I have also been having trouble with it. In my case it works perfectly if it is connected when I boot up and is enabled using Network Manager. However, if I disconnect it at any point while the computer is running and try to connect again later it does not work: Network Manager is no longer able to detect that ethernet is connected. eth0 still shows up when I run ifconfig; but when I try to connect manually using,
```
sudo dhclient eth0
```
the request times out. I can only get an ethernet connection again by rebooting.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
**04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)**
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:55:92:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:257854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:384028096 (366.2 MiB)  TX bytes:8571898 (8.1 MiB)
          Interrupt:18 

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```
(I commented out the stuff in /etc/network/interfaces so that it wouldn't interfere with Network Manager.)

---

### Post by darkdays on 2007-05-05
If you boot with no cable, does it show up in lscpi?
If it doesn't then this might be the cause of my problems and a bad cable/socket might be the trigger.

---

### Post by TheOtherShoe on 2007-05-06
> **darkdays said:**
> If you boot with no cable, does it show up in lscpi?
If it doesn't then this might be the cause of my problems and a bad cable/socket might be the trigger.

It does show up in lspci - even when it is not working. So I guess these are actually different issues.

---

