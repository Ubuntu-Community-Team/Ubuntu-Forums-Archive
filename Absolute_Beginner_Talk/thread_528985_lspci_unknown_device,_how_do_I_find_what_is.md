---
title: "lspci unknown device, how do I find what is?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by buzzmandt on 2007-08-18
lspci brings up  this:
> buzzmandt@ubuntu-main:~$ lspci

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290


How do I figure out what this unknown device is?
should be on board audio, but not sure, it has on board audio but i'm using creative labs pci card audio



here's all lspci:
>  lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


---

### Post by overdrank on 2007-08-18
> **buzzmandt said:**
> lspci brings up  this:

How do I figure out what this unknown device is?
should be on board audio, but not sure, it has on board audio but i'm using creative labs pci card audio



here's all lspci:


HI if you run this command in the terminal 
```
sudo update-pciids
```
This will update your pci ids and hopefully correct the output

---

### Post by buzzmandt on 2007-08-18
ran> buzzmandt@ubuntu-main:~$ sudo update-pciids
--16:40:36--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 126,459 (123K) [text/plain]

100%[=========================================================================================================================================================>] 126,459      134.74K/s             

16:40:37 (134.26 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [126459/126459]

Done.

then
> buzzmandt@ubuntu-main:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
05:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
buzzmandt@ubuntu-main:~$ 

unknown device 6290
any ideas here?

---

### Post by overdrank on 2007-08-18
Well do you have the onboard audio disable in bios, if you are using the PCI sound card.

---

### Post by buzzmandt on 2007-08-18
it's not disabled in bios, i've checked that several times.
couldn't get audio to work so put in the audio card I knew would work
not a big deal tho, as my system is working good.
just a quick question on that, if it's disabled in bios would linux still find the device?

---

### Post by overdrank on 2007-08-18
> **buzzmandt said:**
> it's not disabled in bios, i've checked that several times.
couldn't get audio to work so put in the audio card I knew would work
not a big deal tho, as my system is working good.
just a quick question on that, if it's disabled in bios would linux still find the device?

For me if I disable the lan device it is not detected in lspci. So with your case I would say that ubuntu just does not recognize the device.

---

