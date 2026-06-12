---
title: "Connecting to a wirelesss network"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by CoreOxide on 2008-01-29
I have just installed Ubuntu (7.10) on a laptop with a built in WIFI card. Now, when I press the "connect to a wireless network" I get a window which askes fo a name and some selection (the one set to "none" by default). 
What do I write in the "name" field and what option do I select in the drop down box?

P.S.
It's a Netgear WGR614 v7 router.

Thanks :)

---

### Post by codesplice on 2008-01-29
If it's the window I'm thinking of, Name probably refers to the name of your wifi network, and that dropdown menu refers to the security/encryption enabled on that network.

---

### Post by jan quark on 2008-01-29
here is my configuration you have to type in your data
see pic

---

### Post by CoreOxide on 2008-01-29
It is that window. The problem is I don't know what to do with it :\

Where do I find that data?

---

### Post by jan quark on 2008-01-29
run the following command in the terminal
just type them and press enter

```
sudo iwlist scan
``` this scan your surrounding for active wlan spots, there should be the name of your network 
run them and post the results in this thread pleas

```
ifconfig
```
```
iwconfig
```
```
lspci
```

---

### Post by jan quark on 2008-01-29
after sudo iwlist scan you have to type in your login password and press enter

---

### Post by CoreOxide on 2008-01-29
I ran all of the commands and got this output:

monica@monica-laptop:~$ sudo iwlist scan
[sudo] password for monica:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

monica@monica-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:73:66:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14512 (14.1 KB)  TX bytes:14512 (14.1 KB)

monica@monica-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

monica@monica-laptop:~$ lspci
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
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by prshah on 2008-01-29
Make sure that the wireless switch on your laptop is turned on.

Cheers,
PRShah

---

### Post by the_sorrow on 2008-01-29
Maybe yuor wireless card is not configure for linux, go to System>Adminsitration>Restricted Drivers Manager, if its dsisable, enable it, if it returns an error, please post it here.

---

