---
title: "PCMCIA Wifi Card problems"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Cirdan Alcarin on 2008-03-21
Hello every body, I recently installed Ubuntu 7.10 on a dell Inspiron 1000.  Every thing works fine except for the PCMCIA slot, I have a belkin F5D7010V7 I installed NDISWRAPPER and followed that guide since they had compatible drivers for my card, but there seems to be no power to the card itself.  I then installed PCMCIA-CS and still no luck, I'm totally new to the workings of ubuntu, I only know a few commands and I'll post what I know.  THANKS FOR ANY AND ALL HELP!!!

Results of lshw
cirdan@cirdan-laptop:~$ lshw
WARNING: you should run this program as super-user.
cirdan-laptop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 221MB
     *-cpu
          product: Mobile Intel(R) Celeron(R) CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.9
          size: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KB
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-communication
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic bus_master cap_list
             configuration: driver=Intel ICH Modem latency=173 maxlatency=11 mingnt=52 module=snd_intel8x0m
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:0f:1f:c4:db:0e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.72 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
        *-pcmcia
             description: CardBus bridge
             product: PCI1510 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
     *-network UNCLAIMED
          description: Ethernet controller
          product: Belkin
          vendor: Belkin
          physical id: 0
          bus info: pci@0000:02:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=64 mingnt=32
I hope this helps.

---

### Post by igknighted on 2008-03-21
Hmm... it sees it, but does not recognize it.  I ran an f5d7010 for a while and after a few tries ndiswrapper finally worked... make sure that you blacklist the bcm43xx modules first, as these can interfere with ndiswrapper.  I never got the lights on my card to come on, even when it worked, so since it sees a belkin network card in the pcmcia slot (according to lshw), I think its just the driver.

Which guide did you use to set ndiswrapper up?

---

### Post by Cirdan Alcarin on 2008-03-21
I can't find the guide I used it simply said to download and install NDISWRAPPER here is one of the links I used [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
ok so how do I blacklist the bcm43xx modules? and thanks for the help man!

---

### Post by Cirdan Alcarin on 2008-03-21
so I googled and found this to blacklist things 
```
gksu gedit /etc/modprobe.d/blacklist
```
then I added the line
```
blacklist bcm43xx 
```
and restarted and no affect, my wifi card is not listed in the network manager, and when I go the system-admin-windows wireless drivers and it shows that a driver is installed but that there is no hardware present.  Any ideas?

---

### Post by jan quark on 2008-03-21
please run these commands and post the output:

```
lspci
sudo lshw -C network
iwconfig
sudo iwlist scan
```

---

### Post by aLsanomo on 2008-03-21
How to make it work under Gutsy:

I did some research to identify your chipset. You need to download the following driver and unzip it:

[ftp://210.51.181.211/cn/wlan/Driver_1097_2KXP_0201.rar](ftp://210.51.181.211/cn/wlan/Driver_1097_2KXP_0201.rar)

Once you unzipped it, do the following in the terminal:

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
sudo ndiswrapper -m
sudo ndiswrapper -i net8185.inf (remember to be in the directory where you got the .inf, .sys, .cat unzipped)
sudo ndiswrapper -a 1799:701f net8185
sudo modprobe ndiswrapper
sudo -i
echo ndiswrapper >> /etc/modules

If you get permission denied in this last step, just type "sudo su" to gain root access, and then retry.

Reboot. I didn't have the oportunity to try it out, but it should work.

If problems with ndiswrapper, there's a great guide here: 

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Regards,

---

### Post by Cirdan Alcarin on 2008-03-22
aLsanomo your a genius! it worked!! thanks so much man I now have wifi on my laptop and the lights on the card work like a champ! thanks to all of you who helped me with this.  I'm trying to step away from the evil that is Microsoft! thanks again guys!

---

### Post by aLsanomo on 2008-03-23
> **Cirdan Alcarin said:**
> aLsanomo your a genius! it worked!! thanks so much man I now have wifi on my laptop and the lights on the card work like a champ! thanks to all of you who helped me with this.  I'm trying to step away from the evil that is Microsoft! thanks again guys!

You are very welcome. Enjoy!

---

