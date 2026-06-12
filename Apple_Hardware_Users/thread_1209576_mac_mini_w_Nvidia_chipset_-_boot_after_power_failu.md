---
title: "mac mini w/ Nvidia chipset - boot after power failure"
date: 2009-07-10
forum: Apple Hardware Users
---

### Post by chirhoxi on 2009-07-10
[Background]
I have a older model of the mac mini running Ubuntu 8.10. This particular mini is using the "Santa Rosa" chipset and more specific to my issue is using the 82801GBH I/O controller hub ([http://www.intel.com/design/chipsets/datashts/307013.htm](http://www.intel.com/design/chipsets/datashts/307013.htm)) On this mac mini I can successfully get it to reboot after power is restored following a power failure. This is done by setting the proper register on the I/O controller hub via this command


 sudo setpci -s 0:1f.0 0xa4.b=0


 referenced from ([http://www.mythic-beasts.com/support/macminicolo_howto.html](http://www.mythic-beasts.com/support/macminicolo_howto.html)).
However, I am running Ubuntu 8.04 on the newest 2009 revision of the mac mini. This mac mini uses the NVIDIA 9400M G chipset ([http://www.appleinsider.com/articles/08/10/17/inside_the_new_macbooks_firewire_usb_and_the_nvidia_controller.html](http://www.appleinsider.com/articles/08/10/17/inside_the_new_macbooks_firewire_usb_and_the_nvidia_controller.html)). I can not find any references from a full days efforts on google of anyone getting the newer mac mini's to reboot after power is restored from a power failure.


 [Problem]
I can not find any datasheets/documentation/specification on the NVIDIA chipset used in the newer mac mini in regards to I/O control registers and power management registers so that I can know the proper register to set and what value to set it.


 [Information]
On the older mac mini the out put of lspci is:

#>lspci
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
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
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
 This device [00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)] is the one that I set the AFTER_G3 bit in register 0xa4 and everything works like it should. When power is lost and then restored the system boots.


 On the newer mac mini the output of lspci is


 #> lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 0a82 (rev b1)
00:00.1 RAM memory: nVidia Corporation Unknown device 0a88 (rev b1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 0aae (rev b2)
00:03.1 RAM memory: nVidia Corporation Unknown device 0aa4 (rev b1)
00:03.2 SMBus: nVidia Corporation Unknown device 0aa2 (rev b1)
00:03.3 RAM memory: nVidia Corporation Unknown device 0a89 (rev b1)
00:03.4 RAM memory: nVidia Corporation Unknown device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation Unknown device 0aa3 (rev b1)
00:04.0 USB Controller: nVidia Corporation Unknown device 0aa5 (rev b1)
00:04.1 USB Controller: nVidia Corporation Unknown device 0aa6 (rev b1)
00:06.0 USB Controller: nVidia Corporation Unknown device 0aa7 (rev b1)
00:06.1 USB Controller: nVidia Corporation Unknown device 0aa9 (rev b1)
00:08.0 Audio device: nVidia Corporation Unknown device 0ac0 (rev b1)
00:09.0 PCI bridge: nVidia Corporation Unknown device 0aab (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0ab0 (rev b1)
00:0b.0 IDE interface: nVidia Corporation Unknown device 0ab5 (rev b1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0aa0 (rev b1)
00:15.0 PCI bridge: nVidia Corporation Unknown device 0ac6 (rev b1)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0ac7 (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0861 (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
04:00.0 FireWire (IEEE 1394): Agere Systems Unknown device 5901 (rev 07)


 If I assume that the register layout in Intel and NVIDIA's chipsets are the same then I would just set the device [00:03.0 ISA bridge: nVidia Corporation Unknown device 0aae (rev b2)] with a command such as


 sudo setpci -s 00:03.0 0xa4.b=0


 However the world is not so perfect and this doesn't work. Has anyone had experience with this? I simply need to know what register in the chipset to change via setpci command. Does anyone know which register in the nvidia 9400m (NVIDIA MCP79 chipset family) is used for Power Management, specifically boot on power restore following a power failure.


 Thanks in advanced.

---

### Post by chirhoxi on 2009-07-15
Solution Found!


 I was right in thinking that the device 00:03.0 was the one I needed to manipulate. On a different mac mini running the same chipset the lspci command gave me this:


 00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)


 which is nice but its not necessary to have the lspci command recognize the proper naming of the device. To view a hex dump of this specific device's register use:


 $> sudo lspci -s 00:03.0 -vvvxxxx
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: nVidia Corporation Device cb79
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: I/O ports at 2000 [size=256]
00: de 10 ae 0a 0f 00 a0 00 b2 00 01 06 00 00 80 00
10: 01 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 de 10 79 cb
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: de 10 79 cb 00 00 d0 fe 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 5a 62 02 00 00 00 05 0f 00 fc 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 08 01 01 00
70: 10 00 ff ff cd 00 17 00 00 00 44 59 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 40 03 ff 00 00 00
90: 00 7c 00 00 ff ff 0f 00 00 00 00 00 00 00 00 00
a0: 03 00 00 31 00 00 01 00 00 03 1f 03 00 07 ff 07
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: fd 00 00 00 00 00 00 00 f8 0c 00 fc 00 73 00 30
e0: 83 24 00 2d ac 39 d5 5e 0a 60 da 40 00 00 00 00
f0: ec 00 00 fc fd 00 00 00 10 00 80 80 00 00 00 00


 After much research into this issue here is what you need to do to make it work. The register that handles the functionality we want (boot after power is restored following a power loss) is in 0x7b located on this line


 70: 10 00 ff ff cd 00 17 00 00 00 44 59 00 00 00 00


 0x7b is set to 0x59 currently, if you change this to 0x19 then you will achieve what you want, a boot up when power is restored. Change the register value by using
 sudo setpci -s 00:03.0 0x7b.b=19


 This should only need to be done once, however I don't think it would hurt if the setpci command was placed very early in your start up scripts.

---

### Post by [Q] on 2009-11-08
This is an old topic, but I'd like to thank chirhoxi for figuring this stuff out. I'm currently using my firstgen Mac mini (core duo 1.6 ghz) as a router / download host that should restart once power is restored.

---

### Post by aonicc on 2010-09-22
Does anyone know the register you need to change on the new MCP89 chipset in the Mac Mini 2010 (4-1)? Or how I could figure out which one it is?

Thanks!

---

### Post by aonicc on 2010-09-22
Nevermind. It turns out that it's the same register. Though on my system it was set to 0x60 to begin with. I hope I didn't mess anything up.

---

### Post by salas on 2011-02-16
Hi All,

Did the same steps and it works , however if I reboot the machine all the config is lost
I checked the value of  [FONT=monospace][/FONT]lspci , it has the old values 
I write a small script to put on start up application , but does not solve the problem

Any idea how to have persistent value in the system after reboot

---

### Post by salas on 2011-02-17
[SIZE=2]I am answering my question

[/SIZE][SIZE=2]put this     sudo setpci -s 00:03.0 0x7b.b=19 in any startup script file .sh
[/SIZE][SIZE=2]just make sure to change /etc/sudoers  
[SIZE=1]
[/SIZE][/SIZE][SIZE=1][COLOR=#000000][FONT=Arial]edit /etc/sudoers[/FONT][/COLOR]
[/SIZE][SIZE=1][COLOR=#000000][FONT=Arial]and add:[/FONT][/COLOR]
[/SIZE][SIZE=1][COLOR=#000000][FONT=Arial]username ALL=(ALL) NOPASSWD: ALL[/FONT][/COLOR]
[/SIZE][SIZE=1][COLOR=#000000][FONT=Arial]save and that's it.[/FONT][/COLOR]
[/SIZE][SIZE=1][COLOR=#000000][FONT=Arial]the username is the user you want to give doing sudo without password[/FONT][/COLOR][/SIZE]

---

### Post by chagrins on 2011-06-17
> **chirhoxi said:**
> After much research into this issue here is what you need to do to make it work. The register that handles the functionality we want (boot after power is restored following a power loss) is in 0x7b located on this line

70: 10 00 ff ff cd 00 17 00 00 00 44 59 00 00 00 00

How did you get there? I have a Mac Pro and would like it to reboot after power failure. Seems like there's two steps to getting it to work: (1) figure out which device from the list in lspci is the relevant device; and (2) figure out which register within that device is the relevant register, and what it should be set to.

chirhoxi's solution to (1) (which device) is the "LPC bridge" on the Mac mini. Should I be looking for the "LPC controller" on the Mac Pro?

No idea where to start on (2) (which register).

Does anyone have any clues?

---

### Post by chagrins on 2011-06-18
So I found the datasheets for the Intel 5400 chipset, which the Mac Pro in question uses. On page 191 of the [I/O controller hub datasheet]("http://www.intel.com/Assets/PDF/datasheet/313082.pdf") a table identifies the location of the AFTERG3 bit, the one that controls restart-automatically-after-power-failure functionality:

Bit name: AFTERG3_EN

Register: General PM Configuration 3 Register: GEN_PMCON_3

Location: D31:F0:A4h

Bit: 0

Default value: 0

I want to somehow change this value to 1. But I have no idea how to map the "location" of the relevant bit given in the Intel datasheet to the output of the 'lspci' or 'setpci' commands (which look like chirhoxi's posts above). Anyone have any ideas?

---

### Post by chirhoxi on 2011-06-28
Chagrins,

Good work on investigating the issue. Without digging back into my original post and remembering everything I did I will try to answer your questions of "how" I found the register to change and what value to change it to.

It was actually simpler than it seems and relies on the MAC OS that comes on the MAC system in question. For me it was the MAC Mini. Within the MAC OS there is a system setting (I can't for the life of me remember where it is located in the gui of mac os, but it is somewhere in the system settings, google should help you find where it is). So what you have to do is get the lspci command ported into your mac os. It was a simple download and install through mac ports if I remember. Note this required me to look at a friends mac mini that had the stock OS installed. So if you have another Mac Pro system around or can get a hold of one you need to investigate on that, or reinstall the mac os...

Once you are in the MAC OS and have the mac version of lspci then pull up the register values for the proper device. In my case it was "00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)" so in your case I would look for something similar to "LPC Bridge" or the same numbers "00:03.0" but this is just a guess, the Mac Pro could be configured very differently than the mini.

Given that set of register values as your reference. Go into the gui interfaces and toggle the switch to "reboot after power restore" (or something like that). Once that is toggled re-read the register values and see what is different. The difference is the answer to your question.

Hope that helps

---

### Post by chagrins on 2011-06-29
Great method! Simple but I hadn't thought of it. Many thanks for posting!

---

### Post by enoriel on 2011-07-21
For MacPro solution is same:

root@db:~# lspci -s 00:1f.0 -vvvxxxx
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
        Subsystem: Intel Corporation Device 7270
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Kernel modules: iTCO_wdt, intel-rng
00: 86 80 70 26 07 00 00 02 09 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 70 72
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 01 04 00 00 80 00 00 00 01 05 00 00 10 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 8b 80 8a 89 d0 00 00 00 83 80 8b 8a 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 0f 3c 01 03 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 02 00 00 04 00 00 00 00 00 00 00 00 03 00 00
b0: 00 00 00 00 00 00 00 00 00 00 02 08 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 67 45 00 00 c0 ff 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 01 c0 d1 fe 00 00 00 00 80 0f 01 00 00 00 00 00

The register that handles the reboot functionality is 0xA4

To reboot after power failure run:
sudo setpci -s 00:1f.0 0xA4.b=4

To stay off after power failure run:
sudo setpci -s 00:1f.0 0xA4.b=5

You can put this commands in startup scripts, if you wanna run your MacPro server with Ubuntu always on :)

---

### Post by eti.que on 2011-08-11
Hi board,

Thanks for the trick.

One question though, I'd like my Mac Mini 4,1 to boot each time it sees power (I've got a plug that shuts itself down below a certain amperage level - I'm kinda on an energy saving craze :p), not just after a power loss.

I was wondering if that would work as well ? Or is it a way to cleanly shut down a computer while making the (???) believe it lost power?

---

