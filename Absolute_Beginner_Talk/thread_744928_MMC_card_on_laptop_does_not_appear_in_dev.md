---
title: "MMC card on laptop does not appear in /dev"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by omkarwagh on 2008-04-04
i have a laptop with an mmc card reader. it used to work properly.

however it has suddenly disappeared from /dev.

the output of sudo lshw is below:-
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:08:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:08:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:08:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:08:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=sdhci latency=64 maxlatency=4 mingnt=7 module=sdhci
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:08:08.0
                logical name: eth0
                version: 01
                serial: 00:0f:b0:fd:6e:43
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=10.9.203.8 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


the complete out-put of lshw is attached with this post.

thanks in advance.

---

