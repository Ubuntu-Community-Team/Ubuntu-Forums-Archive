---
title: "Wireless internet"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Racer_X_ on 2007-02-16
I just instlled ubuntu 6.06.  I need to be able to connect to my wireless network.  I dont have  a clue on how to do this using this type of o/s, So I guess my question would be how do I get a list of wireless networks??

Also my laptop has a built in wireless card if that helps any.

---

### Post by ComplexNumber on 2007-02-16
do you know what the exact make and model of your wireless card is?

---

### Post by Racer_X_ on 2007-02-16
> **ComplexNumber said:**
> do you know what the exact make and model of your wireless card is?

no i dont all i know is that it is an internal one, and it is a gateway computer.

---

### Post by Racer_X_ on 2007-02-16
anybody???

---

### Post by mikewhatever on 2007-02-16
This command 'lshw' typed in the terminal will list all of your hardware. It should be a rather large list, but your wireless card is there for sure. You'll need its model if it doesn't work.
Assuming it does work, you can go to System->Administration->Networking, and enter the network informations in the properties of the Wireless Connection. If there is no Wireless Connection, use lshw command. 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
To chose wireless networks, you'll need to install a network manager, such as sudo apt-get install network-manager-gnome. Of cause that requires internet connection.
Oh, and remember, patience is our big friend. :)

---

### Post by Racer_X_ on 2007-02-16
> **mikewhatever said:**
> This command 'lshw' typed in the terminal will list all of your hardware. It should be a rather large list, but your wireless card is there for sure. You'll need its model if it doesn't work.
Assuming it does work, you can go to System->Administration->Networking, and enter the network informations in the properties of the Wireless Connection. If there is no Wireless Connection, use lshw command. 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
To chose wireless networks, you'll need to install a network manager, such as sudo apt-get install network-manager-gnome. Of cause that requires internet connection.
Oh, and remember, patience is our big friend. :)


ok so im REALLY new to ubuntu im used to windows.  this is guna sound stupid but by "terminal" what do you mean?? i looked at the link you gave me but it only says that i have ethernet connection and modem connection nothing with wireless.

---

### Post by darrenm on 2007-02-16
Terminal is Applications > Accessories > Terminal, just like the ms-dos prompt in Windows.

In the terminal window type lspci and press return

Then select all of the text, go to edit, click copy then when replying on this thread right click and choose paste. :)

---

### Post by mikewhatever on 2007-02-16
No problem, Racer_X, we all start from about the same level. The terminal is the place/window to type commands, and you can find it in Application->Accessories->Terminal. You're gonna need it a lot if you stick with Ubuntu, so if you want, right click on Terminal in the menu, an add the icon to the panel.

---

### Post by Racer_X_ on 2007-02-16
@jesse-laptop:~$ lshw
WARNING: you should run this program as super-user.
jesse-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 766MB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-50
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.8.2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c0000000-cfffffff ioport:9000-90ff iomemory: b0100000-b010ffff irq:10
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 14
                serial: 00:e0:b8:b9:0b:d2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 multicast=yes
                resources: iomemory:b0200000-b0203fff ioport:a000-a0ff irq:233
        *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:b0300000-b0303fff irq:11
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:b0004000-b0004fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-26-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:b0005000-b0005fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-26-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:b0006000-b0006fff irq:225
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:8400-840f iomemory:fed00000-fed003ff
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE
             resources: ioport:8410-841f irq:217
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: HTS421212H9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 111GB
              *-cdrom
                   product: HL-DT-ST DVD-RW GWA-4082N
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capabilities: packet
        *-multimedia
             description: Multimedia controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:b0000000-b0003fff irq:217
        *-isa UNCLAIMED
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-pcmcia
                description: CardBus bridge
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@08:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:b0404000-b0404fff irq:185
           *-firewire
                description: FireWire (IEEE 1394)
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 9.1
                bus info: pci@08:09.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:b0405000-b04057ff iomemory:b0400000-b0403fff  irq:177
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@08:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                resources: iomemory:b0406000-b0406fff irq:11
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
jesse@jesse-laptop:~$

---

### Post by darrenm on 2007-02-16
You have a Broadcom wireless adapter. Same as both of my laptops. It won't be easy unfortunately. Do you have a wired internet connection that works?

---

### Post by Racer_X_ on 2007-02-16
for the time being yes i do have an active connection but only for about an hour cause im at school

---

### Post by Racer_X_ on 2007-02-16
so does anybody know about the broadcom internal wireless adapters and how to get them to work on ubuntu?

---

### Post by Racer_X_ on 2007-02-16
?????????????

---

### Post by meborc on 2007-02-16
this might help: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by Racer_X_ on 2007-02-16
nope didt do anything

---

### Post by mikewhatever on 2007-02-16
Racer_x,
most probably, there is no simple solution of 2-3 steps for your type of wireless card. It is known to be a troublesome one. Luck for me, I have a different one, so can't offer much help. There are lost of howtos to fix things. The one meborc offered looks good. Try reading for longer then 20 minutes, you'll become a small Broadcom expert and probably solve it. Here is a more general troubleshooting guide
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

good luck and don't forget to update

---

