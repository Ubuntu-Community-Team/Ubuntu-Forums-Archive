---
title: "[SOLVED] Followed tips to enable desktop effects and now everything is way slow"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-13
I am running a year and a half old Presario V2000 notebook with an AMD Turion processor. I am not sure of the rest of the specs as I can 't seem to remember what to code to get the hardware list to pop up in terminal. Anyway, I was having a problem getting desktop effects enabled and someone pointed me to an awesomely simple and useful thread 

[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m)

Anyway, after I followed the instructions I was able to get desktop effects to enable but now everything is impossibly slow. I even went back and disabled them but I still am having a hard time even scrolling up and down in windows.

---

### Post by Pumalite on 2007-12-13
Did you notice this:
'Fixed the problem. Word of warning: the ATI 42.x.3 (whatever the latest one is as of 11/25/07) sucks. I downgraded the driver to get things to run smoothly.'
__________________

---

### Post by boriquajake on 2007-12-13
> **Pumalite said:**
> Did you notice this:
'Fixed the problem. Word of warning: the ATI 42.x.3 (whatever the latest one is as of 11/25/07) sucks. I downgraded the driver to get things to run smoothly.'
__________________

Thanks, man, no I did not see that. How do I downgrade a driver?

---

### Post by boriquajake on 2007-12-13
By the way, let me just say that guides like the one I followed are the coolest things I have ever seen. That kind of simple, useful help doesn't exist outside of the linux world.

---

### Post by Pumalite on 2007-12-13
Visit the ATI site and follow instructions.

---

### Post by boriquajake on 2007-12-14
> **Pumalite said:**
> Visit the ATI site and follow instructions.

I am nowhere near experienced enough to just go to their site and fix this.

---

### Post by boriquajake on 2007-12-14
OK, I was able to find and download the version of the driver that came out before the most recent one. Now, how do I install it?

---

### Post by hyper_ch on 2007-12-14
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html)

---

### Post by boriquajake on 2007-12-14
I am just making things worse and worse. I am to the point now where it takes me 30 seconds to scroll down two or three paragraphs. I am systematically destroying my systems already weak graphics capability.

---

### Post by Pumalite on 2007-12-14
Post:
lshw

---

### Post by boriquajake on 2007-12-14
> **Pumalite said:**
> Post:
lshw

What in the hell does that mean? Maybe I should just google it?

---

### Post by philinux on 2007-12-14
He means open a terminal and type

[FONT="Courier New"]lshw[/FONT]
and post the results back here!

---

### Post by boriquajake on 2007-12-14
Dangit, you are making me stretch. Just when I had gotten good and spoiled by all those "so easy and idiot like me can follow them" just paste this in terminal tips you come along and actually expect me to think.

Here, this is what happened when I entered lhsw in terminal:

>  description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 894MB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-34
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: FUJITSU MHV2120AT PL
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 111GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: HL-DT-ST DVDRAM GSA-4084N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 10
                serial: 00:16:36:93:3d:35
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.10.162 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-network:1
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:7f:13:c0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-386 latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:05:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:05:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:05:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 9.4
                bus info: pci@0000:05:09.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=4 mingnt=7 module=sdhci
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp


Is this what you meant I should do?

---

### Post by boriquajake on 2007-12-14
You know, I realize that I was being an ungrateful dick. I am sorry. Thank you for taking the time to help me out, I appreciate it.

---

### Post by Pumalite on 2007-12-14
Your system seems OK. No reason for slow down. You have enough memory. Are you running out of space?
Post:
df -h

---

### Post by boriquajake on 2007-12-14
> **Pumalite said:**
> Your system seems OK. No reason for slow down. You have enough memory. Are you running out of space?
Post:
df -h

Nope, I have at least 50% of my HDD available, probably more. This only started after I followed a how to thread to get compiz working. It worked (up until then when I tried to "enable desktop effect" I got an error message) but everything slowed down to where it was unusable. Of course I went back into preferences and set desktop effects back to "none"  but still it is like I no longer have a graphics card working at all or something.

---

### Post by boriquajake on 2007-12-15
I did a re-install of Gutsy and then followed the same instructions that seemed to have triggered the problems last time and now everything works freaking awesome. It must have been something stupid that I did. I mean, I guess that is obvious. Anyway, thanks to all for you help.

---

