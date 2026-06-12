---
title: "Is the wireless card destroyed?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-03-12
The day before yesterday, I installed Ubuntu Dapper on a laptop (Acer aspire 2310). The wireless card (atheros-chipset) was detected when running the live-cd, and after typing in essid and wep-code, the card just worked. Everything was well for about 24 hours. The wireless card and my router worked happily together. Yesterday, however, I noticed that the laptop froze after hibernation. Nothing worked, not even control+alt+backspace. Had to do a hard reboot. When I restarted the computer, the wireless connection did not work. I opened up the network manager, and the wireless connection was gone. Trying to get some more information, i typed iwconfig and found that Ubuntu didn`t see any wireless devices. Finally, I tried to boot from the live-cd, and the wireless card was not even detected there! 

I suspect that the wireless card is destroyed, but I don`t really want to buy a new one if there is anything I can do to fix the problem.



Hallvor

---

### Post by siciliancasanova on 2007-03-12
What is your output when you type in ```
lspci
```


If the card is not showing up, try going [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and going down to section 4.1.2.  It is a troubleshooting section on non-recognized cards.

---

### Post by Hallvor on 2007-03-12
OK. Here it is:
> 
ragnhild@ragnhild-laptop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
ragnhild@ragnhild-laptop:~$

---

### Post by siciliancasanova on 2007-03-12
Yes the card is not listed there.  I have only used ubuntu/linux for 5 days but I will say that on my machine my Broadcom is listed as a "Network Controller" which you clearly don't have listed.  

I searched google for **wireless card not showing up lspci** and there were quite a few forum topics across the linux distros with your problem.  Didn't seem like a lot of solutions but there are a few more things they suggested you try before you go out and buy a new card.

---

### Post by AtrejuT on 2007-03-12
are you sure?
my guess is that this here:
```

0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
```

is the wireless card? at least atheros does make chipsets for wireless cards, but that's all I know.
maybe you can look around the forums for help/problems installing atheros cards?

atreju

---

### Post by siciliancasanova on 2007-03-12
I thought that was the Network Interface Card but I'm no hardware guy.

---

### Post by dhughes on 2007-03-12
> **Hallvor said:**
> OK. Here it is:

 agnhild@ragnhild-laptop:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
**0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)**
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
**0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)**
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
ragnhild@ragnhild-laptop:~$

 It looks like both your ethernet card and your wireless card are being recognized.

 I had a similar problem, I installed Dapper on an older desktop system, my integrated ethernet card was found and then it just disappeared. I had a spare PCI ethernet card but that didn't work. I forget but I think I found them with lspci but I didn't find the cause other than upgrading to Ubuntu Edgy.

---

### Post by siciliancasanova on 2007-03-12
Yes, I need glasses.

---

### Post by Hallvor on 2007-03-13
Instead of a full upgrade (that might not solve the problem), should the edgy live-cd detect the card? Will it give the same networking results as a full install? I`m just trying to save time.


Hallvor

---

### Post by siciliancasanova on 2007-03-13
If it's not located in iwconfig then in my experience that would point to a firmware problem, it is recognized in lspci says that somethings plugged into your machine but the device is unknown.

---

### Post by Hallvor on 2007-03-13
That makes sense.

---

### Post by imog on 2007-03-13
Since both controllers are recognized, its just a software problem with the Wireless NIC - the drivers are corrupted after your machine locked up and hard rebooted.  If you could reload them your problem should be resolved (from a windows perspective, not sure if there are extra steps in Ubuntu other than reloading the drivers).  To be most clear - your hardware is fine and you do not need to replace the wireless NIC.  You need to fix the software problem.

My second thought is that I cannot explain why it would not work in the Live CD anymore.  We can ignore that until someone instructs you how to reload the drivers, then if your card is still not working maybe it becomes pertinent.

Finally, I just wanted to comment to clarify that it is not a firmware problem with your card.  Firmware is stored on FLASH rom on the NIC itself and is completely different than a software driver issue.  The card firmware is fine, but the drivers that the OS uses to interface with the card are screwed up.  Drivers are software and can get corrupted pretty easily, firmware rarely gets corrupted unless you are in the middle of flashing it and there is a crash.

I'm a Windows system tech so I know how to recognize the problem, but I do not know how to tell you to fix it in Ubuntu - I've only got 3 days under my belt so far, but things are going very well for me.  Hope this is helpful.

---

### Post by Hallvor on 2007-03-13
Problem solved. Rebooted with an Edgy cd and the card was recognised again. I read somewhere that the madwifi driver doesn`t like wep-encryption, so just in case I`ll turn wep encryption off and use a mac-filter instead. (Never happened that anyone has tried to get access to my router, even when the encryption was off.)

---

### Post by Hallvor on 2007-03-23
.... and the problem is back - this time under Edgy... :( I`ll post some messages from the log later.

---

### Post by Hallvor on 2007-03-23
OK. Here they are. Acer travelmate 2310 laptop running Edgy, but also had the same problem in Dapper.

This is from /var/log/user.log

> Mar 22 20:28:20 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar 22 20:28:20 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar 22 20:28:27 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar 22 20:28:27 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Mar 22 20:28:27 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar 22 20:28:27 ragnhild-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers


messages.log

> Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.512000] ath_hal: module license 'Proprietary' taints kernel.
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.512000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.556000] Linux agpgart interface v0.101 (c) Dave Jones
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.596000] agpgart: Detected SiS 661 chipset
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.596000] agpgart: AGP aperture is 32M @ 0xe0000000
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.632000] wlan: 0.8.4.2 (0.9.2.1)
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.632000] ath_rate_sample: 1.2 (0.9.2.1)
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.640000] ath_pci: 0.9.4.5 (0.9.2.1)
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.640000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.640000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.640000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Mar 22 20:09:34 ragnhild-laptop kernel: [17179589.956000] input: PC Speaker as /class/input/input1
Mar 22 20:09:34 ragnhild-laptop kernel: [17179590.100000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
Mar 22 20:09:34 ragnhild-laptop kernel: [17179590.100000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0082]

kern.log


> Mar 23 05:36:22 ragnhild-laptop kernel: [17179577.232000] kjournald starting.  Commit interval 5 seconds
Mar 23 05:36:22 ragnhild-laptop kernel: [17179577.232000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.648000] ath_hal: module license 'Proprietary' taints kernel.
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.648000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.840000] wlan: 0.8.4.2 (0.9.2.1)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.844000] ath_rate_sample: 1.2 (0.9.2.1)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.848000] ath_pci: 0.9.4.5 (0.9.2.1)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.852000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.852000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.852000] wifi%%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
Mar 23 05:36:22 ragnhild-laptop kernel: [17179589.852000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.508000] sis900.c: v1.08.09 Sep. 19 2005
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.508000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 177
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.516000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.520000] 0000:00:04.0: Using transceiver found at address 13 as default
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.520000] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 177, 00:c0:9f:b3:a7:90.
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.540000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
Mar 23 05:36:22 ragnhild-laptop kernel: [17179590.540000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0082]

lspci output:

> ragnhild@ragnhild-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
ragnhild@ragnhild-laptop:~$ 

output of iwconfig

> ragnhild@ragnhild-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


So... What is wrong?

---

### Post by Hallvor on 2007-03-24
Anyone?

---

### Post by ramzai on 2007-03-24
Maybe [Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) can help? And have a look at other documents in the [WiFi Section](https://help.ubuntu.com/community/WifiDocs/).

---

### Post by Hallvor on 2007-03-28
Finally got it working again. It was apparently a bug in the old madwifi driver, so after updating madwifi to the latest version at sourceforge it works again.

---

