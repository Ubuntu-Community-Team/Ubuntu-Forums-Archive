---
title: "Programs not detecting webcam dispite having a driver"
date: 2018-04-05
forum: Apple Hardware Users
---

### Post by disreputabledog on 2018-04-05
Ubuntu 16.04 running on a macbook air.

Skype and Cheese cannot detect my webcam, but when I do lshw;

```
           
*-multimedia
                description: Multimedia controller
                product: 720p FaceTime HD Camera
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bdc-pci latency=0
                resources: irq:52 memory:c1500000-c150ffff memory:a0000000-afffffff memory:c1400000-c14fffff


```

Which means it does have a driver right? 
But the program still doesn&#8217;t see it;
[ATTACH=CONFIG]279178[/ATTACH]

What could I do to try and fix it?

---

### Post by wildmanne39 on 2018-04-05
*Thread moved to **Apple Hardware Users, a more appropriate forum**.*

---

