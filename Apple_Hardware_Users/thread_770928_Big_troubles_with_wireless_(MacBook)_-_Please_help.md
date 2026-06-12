---
title: "Big troubles with wireless (MacBook) - Please help!!!"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by arseniy on 2008-04-27
I've been working on this for like two days and still can't get it. So I turn here.

Here's the story: I installed Gutsy on a MacBook (clean install, nothing but Ubuntu is present). I downloaded and installed successfully ndiswrapper (1.52). I downloaded the Atheros wireless card driver that someone posted online (coming from the Boot Camp "Windows Drivers" that you get when you use Boot Camp to make the second partition). I unrar-ed that driver (AtherosXPInstaller.exe) and got a whole bunch of stuff extracted to a directory I made for it (~/atheros), including "net5416.inf". So I opened a Terminal and ran this:

```
sudo ndiswrapper -i ../atheros/net5416.inf
```

and got this output:

```
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
```

so everything was installed fine. I even checked it with:

```
sudo ndiswrapper -l
```

and got:

```
net5416 : driver installed
```

so everything *was* fine. Then I did ```
sudo modprobe ndiswrapper
``` like the instructions I was following told me to do, and all was fine. But here's the weird part... I run ```
iwconfig
``` and all I see is:

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

Does this mean that my wireless card is broken or something? Why can't iwconfig see it???

Here's some more information. MacBook 13" Core 2 Duo 2.0GHz, 2.0GB RAM. And here's some history that I hope will help:

Before ndiswrapper (and the cause of me having to install ndiswrapper) was an attempt at madwifi. I downloaded, made, and install version 0.9.4, and I did everything up to this next step correctly. I ran ```
modprobe ath_pci
``` and that was fine, and then I did this:

```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

and it said something like (I can't say exactly b/c I don't have it now) "cannot *verb* ioctl: No such device".

Please help!

---

### Post by dustynus on 2008-04-27
if your using the amd64 version of ubuntu, you can't use ndiswrapper with that card. There is no 64 bit version of the drivers in windows.

If this is the case, you need to use madwifi drivers.

---

### Post by cyberdork33 on 2008-04-27
Please post your Macbok version. The newest Macbooks do not have an atheros card, but rather, a broadcom card. Check the output of lspci to verify.

The output of 'ndiswrapper -l' should also say that matching hardware was found for that driver...

---

### Post by arseniy on 2008-04-27
Output of lspci is:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```

It's a 2.0GHz MacBook, Core 2 Duo. Idk what details to give lol :)

And ndiswrapper -l says:
```
arseniy@Arseniy-MacBook:~$ ndiswrapper -l
net5416 : driver installed
```

---

### Post by cyberdork33 on 2008-04-27
```
Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```you defintely have an atheros card...

Are you using 64 bit ubuntu?

---

### Post by arseniy on 2008-04-27
How do I check that? My computer supports it but I don't exactly know if I am using it.

---

### Post by arseniy on 2008-04-28
AHA EUREKA! I don't know how/why it worked now, but here's what I did, after upgrading to 8.04 and following the instructions **benanzo** gave me:

***upgrade to 8.04***
```
cd /home/arseniy/Desktop/madwifi
make
sudo make install
sudo depmod -ae
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

Then, running ```
iwconfig
```, I get:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And wireless now works. W00t! But I still need a bit of advice. The last time this worked, I was able to use it for two boots, after the second of which I was no longer able to see the ath0 thing, nor use wireless of any form. Is this a recurring problem? Is this a bug? Is there a way to somehow put some code into an init script so that on every boot, madwifi will *definitely* work?

---

### Post by benanzo on 2008-04-28
Hi arseniy,

Sorry I wasn't available after you upgraded to Hardy, I had to drop off for a bit.  Your wireless *should* work indefinitely now that you've upgraded to a stable kernel in an LTS release (Hardy).  However, if for some reason Ubuntu updates the kernel then your wireless will stop working until you recompile madwifi.  Just follow the same instructions you did earlier to get it going or see [here]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25").  Also, if for any other reason (aside from a  kernel upgrade) your wifi stops working, just issue these two commands:
```

$ sudo modprobe -r ath_pci
$ sudo modprobe ath_pci

```
That will reload the driver and recreate the wireless devices (wifi0,ath0).

Good Luck!

---

