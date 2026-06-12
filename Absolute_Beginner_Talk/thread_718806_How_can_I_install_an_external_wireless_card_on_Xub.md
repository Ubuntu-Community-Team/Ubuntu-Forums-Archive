---
title: "How can I install an external wireless card on Xubuntu?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-08
hi, I recently installed Xubuntu on an older laptop, and am now having the issue of installing an external wireless card. The cards I have are SMC (model No: SMC2635W), and a Belkin (Model No: F5D7010). I am fine with using either one, and I have the install CD's for both of them. Do I need to use wine to install it, because Xubuntu is taking the full partition, and that would not be possible. Is there anything I can do?

Thanks,
CloudFX:)

---

### Post by ugm6hr on 2008-03-08
Both of those cards come in different versions, with different chipsets.

With one of them plugged in, run the 2 commands and post the output.

Then do the same with the other plugged in.

```
lspci
lshw -C network
```

---

### Post by CloudFX on 2008-03-08
Here is the SMC info:

```
nick@NickPC2:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:04.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
nick@NickPC2:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:04.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 20)
```


```
nick@NickPC2:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:36:82:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.103 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=128 mingnt=64
```



And the Belkin:


```
lsnick@NickPC2:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:04.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
```


```
nick@NickPC2:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:36:82:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.103 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:11:50:d9:18:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

---

### Post by ugm6hr on 2008-03-08
Judging by those outputs, the Belkin has an Atheros chipset.  It has also automatically loaded the appropriate driver.

So best to try with that one first.

Some more info is in order - what encryption do you use?  Do you use MAC filtering? Do you "hide" your SSID?

For starters, turn off all security, just to see whether you can find the router.  You can reinstate it  again after the test.

What software do you use to connect in Xubuntu (e.g. Network Manager, Wicd...)? What version of Xubuntu is it?

Try the following commands (with security off) and post the output:
```
ifconfig
iwconfig
```

PS:
Just for info - the SMC card needs ndiwsrapper - see no 14 here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)
Ndiswrapper can be installed from Synaptic (search for ndis-gtk)

---

### Post by CloudFX on 2008-03-08
Thanks for your help. I'll use the Belkin one then. 

To answer the questions:

I use Mac filtering
SSID is hidden
I believe that I use Network Manager
I'm using Gutsy 32bit

I'm on another computer right now, and will be back on that later. I'll do the rest then:)

---

### Post by ugm6hr on 2008-03-09
Hidden SSID is your problem.  Network Manager (NM) does not like them at all.  Although it pretends to give that option, I don't know that it works at all.

There are lots of debates about the security benefit of hiding your SSID, and my interpretation is that it will prevent people who don't know anything about wifi security accidentally connecting to your router, but nothing more.

Actually, the same applies to MAC filtering too.

I would recommend WPA / WPA2, although I am not a security expert.

But if you want to stick with an unencrypted wifi with MAC / hidden SSID as the only security, I would suggest uninstalling Network Manager and using Wicd (see the signature link below).

Anyway - try the Belkin with MAC / SSID off, and NM should be able to connect.

If we know that, then at least we know that we are on the right track.

---

### Post by CloudFX on 2008-03-09
Unfortunately, I don't have network permissions, and I can't try that. Is that going to be an issue?

I will try installing Wicd.

---

### Post by ugm6hr on 2008-03-10
> **CloudFX said:**
> Unfortunately, I don't have network permissions, and I can't try that. Is that going to be an issue?

Probably not.

But presumably the network administrator has already includud the Belkin's MAC address?  If not, then - Yes - it will be a problem.

Wicd is a good option.

If that doesn't work, try this: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by CloudFX on 2008-03-10
Yea, the Belkin Mac should be in it. If it's not then it can be put in it. I'll try Wicd.

---

