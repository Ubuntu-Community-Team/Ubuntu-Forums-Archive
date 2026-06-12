---
title: "system info for dummies?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-21
Hi, I asked about this a while back but am having trouble finding it again. I just installed Ubuntu 7.10 64 bit. I am trying to find useful hardware information like the type, manufacturer, speed, CAS latency of memory. I have tried hwinfo, hardinfo, sysinfo, lshw, device manager, and dmidecode. Also tried System>preferences>hardware information.

None of these actually tells me anything like (Dimm, DDR2, Cas latency 3, xxxMHz). You know the stuff you need to buy the right replacement RAM or upgrade? Actually one of them said DIMM but that was all. Everything else in all of the programs is about the memory controller and not the memory. Similar problems finding info on motherboard and BIOS but was able to find some info that I understood on those. Actually went back to windows and ran CPU-Z to get info last time.

I don't have a clue what any of the info those programs give me means, other than available and useable memory but that doesn't help me. 

Thanks to anyone who can enlighten me. :-)

---

### Post by p_quarles on 2008-03-21
Hmm. lshw should list all of that information. Can you post what it says about the memory here?

---

### Post by iansane on 2008-03-21
OK well I appolagize if I'm missing something here. This is the output with the part about usb and harddrives excluded to save space.

```
    description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 4
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket 939
          size: 2200MHz
          capacity: 3GHz
          clock: 201MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0

```

I don't know if it's not reading my system right or if I don't know what I'm reading.

I'm pretty sure according to CPU-Z in Windows it was something like DDR2 PC400 Cas Latency 3. I see latency 0 and 66MHz? but don't know what that's about and no DDR2 or DDR3. Thanks for looking at it.

---

### Post by iansane on 2008-03-21
bump

Anyone? please

---

### Post by Herno on 2008-03-21
did u use sudo ?

---

### Post by iansane on 2008-03-21
I don't think I did the first time but I just now did and got the exact same results

---

