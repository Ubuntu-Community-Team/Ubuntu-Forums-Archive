---
title: "8GB RAM Upgrade On A Gateway NV55C54U - 12.04"
date: 2013-08-11
forum: Any Other OS
---

### Post by giltonq on 2013-08-11
I recently purchased 8GB of [corsair RAM]("http://www.amazon.com/gp/product/B002YUF8ZG/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1") from Amazon for my [NV55C54U]("http://us.gateway.com/gw/en/US/content/model/LX.WSG02.055") laptop. I know that is is compatible, I previously had 4GB. My laptop IS 64-bit and I have a 64 bit variant installed. When I boot up, everything works as normal, but it tells me I have 3.54 GB installed, like usual. I checked in the BIOS and it also says I have 4GB. What do I do? I am relatively new to Ubuntu (6 months of use). If it's helpful, I am actually running Elementary OS Luna, which is based on 12.04. The laptop has a 320 GB hard drive, and a core i3 M370, at 2.40 GHz.

---

### Post by Cheesemill on 2013-08-11
*Thread moved to **Other OS/Distro Support**.*

If it's not even being detected by your BIOS then it isn't an OS issue. Are you sure the RAM is installed correctly?

Can you run the following commands and post the output of the second one please.

```
sudo apt-get install dmidecode
sudo dmidecode --type memory
```

---

### Post by sanderj on 2013-08-11
> **giltonq said:**
> I recently purchased 8GB of [corsair RAM]("http://www.amazon.com/gp/product/B002YUF8ZG/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1") from Amazon for my [NV55C54U]("http://us.gateway.com/gw/en/US/content/model/LX.WSG02.055") laptop. I know that is is compatible, I previously had 4GB. My laptop IS 64-bit and I have a 64 bit variant installed. When I boot up, everything works as normal, but it tells me I have 3.54 GB installed, like usual. I checked in the BIOS and it also says I have 4GB. What do I do? I am relatively new to Ubuntu (6 months of use). If it's helpful, I am actually running Elementary OS Luna, which is based on 12.04. The laptop has a 320 GB hard drive, and a core i3 M370, at 2.40 GHz.

Open a terminal, and do this:

```
wget http://www.appelboor.com/dump/check-my-memory.py
sudo python check-my-memory.py 

```

... that will tell all.

---

### Post by giltonq on 2013-08-12
Sorry for the late reply, here is the output of the command you asked me to run Cheesemill.

```
# dmidecode 2.11SMBIOS 2.6 present.


Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: No Error
    Number Of Devices: 2


Handle 0x001B, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: 0x001D
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: Not Specified
    Serial Number: 00000000
    Asset Tag: Unknown
    Part Number: CMSO4GX3M1A1333C9 
    Rank: Unknown


Handle 0x001C, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: None
    Current Speed: Unknown
    Type: DIMM
    Installed Size: 4096 MB (Single-bank Connection)
    Enabled Size: 4096 MB (Single-bank Connection)
    Error Status: OK


Handle 0x001F, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Unknown
    Part Number: Not Specified
    Rank: Unknown


Handle 0x0020, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: None
    Current Speed: Unknown
    Type: None
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK


Handle 0x0023, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        Unknown
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 8192 MB
    Maximum Total Memory Size: 16384 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        Other
    Memory Module Voltage: Unknown
    Associated Memory Slots: 2
        0x001C
        0x0020
    Enabled Error Correcting Capabilities:
        None

```

Sanderj,

```
check-my-memory.py - version: SJ 2013-02-22OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 1 memory module(s)
BIOS offers 3765 MB as usable
Memory seen by OS 3629 MB
BIOS version 08/10/2011
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit


SUMMARY:
Memory difference between DIMM hardware and BIOS offering 331 MB
Memory difference between BIOS offering and memory seen by OS 136 MB
Memory difference between DIMM hardware and memory seen by OS 467 MB


ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory


Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
          size: 4GiB
          description: [empty]
       description: L3 cache
       size: 3MiB
       capacity: 3MiB
       description: L2 cache
       size: 256KiB
       capacity: 256KiB
       description: L1 cache
       size: 32KiB
       capacity: 32KiB
       description: L1 cache
       size: 32KiB
       capacity: 32KiB


Finished



```

---

### Post by sanderj on 2013-08-13
"Total of physical memory modules found 4096 MB in 1 memory module(s)", so only one SIMM is detected. I would do this:

- remove one SIMM and leave in only one SIMM (SIMM A), boot, and see if it is detected and run the script
- replace the SIMM with the other SIMM (SIMM B), and see if it is detected and run the script
If a SIMM is not detected, also place it in the other memory location, and test again.

Hopefully these tests make clear what is happening.

---

### Post by giltonq on 2013-08-13
> **sanderj said:**
> "Total of physical memory modules found 4096 MB in 1 memory module(s)", so only one SIMM is detected. I would do this:

- remove one SIMM (SIMM A), boot, and see if it is detected and run the script
- replace the SIMM with the other SIMM (SIMM B), and see if it is detected and run the script
If a SIMM is not detected, also place it in the other memory location, and test again.

Hopefully these tests make clear what is happening.

Ok, I will do this tomorrow... Thanks.

---

### Post by giltonq on 2013-08-13
> **sanderj said:**
> "Total of physical memory modules found 4096 MB in 1 memory module(s)", so only one SIMM is detected. I would do this:

- remove one SIMM and leave in only one SIMM (SIMM A), boot, and see if it is detected and run the script
- replace the SIMM with the other SIMM (SIMM B), and see if it is detected and run the script
If a SIMM is not detected, also place it in the other memory location, and test again.

Hopefully these tests make clear what is happening.

Thanks! I switched the location of the modules and now, for some reason elementary now recognizes 8 GBs of ram. I will mark this thread as solved.

---

### Post by sanderj on 2013-08-14
> **giltonq said:**
> Thanks! I switched the location of the modules and now, for some reason elementary now recognizes 8 GBs of ram. I will mark this thread as solved.

It might have been a bad connection. Good that it works, and that you reported that back.

---

