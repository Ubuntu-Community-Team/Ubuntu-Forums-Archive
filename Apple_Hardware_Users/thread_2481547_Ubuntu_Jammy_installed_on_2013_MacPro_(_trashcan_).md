---
title: "Ubuntu Jammy installed on 2013 MacPro ( trashcan ) AMDGPU problems."
date: 2022-12-02
forum: Apple Hardware Users
---

### Post by trapper1204 on 2022-12-02
As the title states, I have installed Ubuntu 22.04 Jammy, on a 2013 MacPro. I have everything working except GPU acceleration.

lash -c video reports *-display UNCLAIMED, product: Tahiti LE [Radeon HD 7870 XT], configuration: latency=0

Of course there were a lot more lines... but should Display be claimed, and could configuration show amdgpu instead of latency=0.

Searching google for a solution had me jumping through all kinds of hoops, installing amdgpu, rocm and a few other utilities. 
Nothing I have done to get Ubuntu to use the amdgpu driver is working.


I need hardware acceleration on this machine as it is a plex sever doing a lot of video transcoding. I also use it for work, and I can't use any virtual backgrounds in my video conferences without the hardware acceleration.

Even, if I did not use plex, or use it for video conferences, the machine has 2 of those GPU's in it, and it would be nice to be able to take advantage of them.

Here is a link to the hardware specs on my desktop.
[https://everymac.com/systems/apple/mac_pro/specs/mac-pro-twelve-core-2.7-xeon-e5-gray-black-cylinder-late-2013-specs.html](https://everymac.com/systems/apple/mac_pro/specs/mac-pro-twelve-core-2.7-xeon-e5-gray-black-cylinder-late-2013-specs.html)

I could really use some help from an Ubuntu/AMDGpu guru.


[FONT=arial]---------- Video Details from 'lshw':


  ```
*-display UNCLAIMED
       description: VGA compatible controller
       product: Tahiti LE [Radeon HD 7870 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: 
           memory:80000000-8fffffff 
           memory:a0700000-a073ffff 
           ioport:3000(size=256) 
           memory:a0740000-a075ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Tahiti LE [Radeon HD 7870 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: 
           memory:90000000-9fffffff 
           memory:a0600000-a063ffff 
           ioport:2000(size=256) 
           memory:a0640000-a065ffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080
```[/FONT]

---

### Post by slickymaster on 2022-12-02
*Thread moved to **Apple Hardware Users**.*

---

