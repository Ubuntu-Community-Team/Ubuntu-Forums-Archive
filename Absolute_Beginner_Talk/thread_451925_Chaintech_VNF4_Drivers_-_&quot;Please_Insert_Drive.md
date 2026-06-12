---
title: "Chaintech VNF4 Drivers - &quot;Please Insert Driver Disk&quot;"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stpieraf on 2007-05-22
Following up with a previous post, I'm having issues installing Ubuntu. After verifying disk integrity, I get the promp "Please Insert Driver Disk".

I'm guessing it's an issue with my motherboard. I'm trying to find drivers for my motherboard. 

Specs:
Chaintech VNF4/Ultra
Model NF-CK804

NVidia offers drivers for the NForce chipset for the following Linux distributions:

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

    * SLES 9 SP3 (2.6.5-7.244)
    * SLES 9 SP2 (2.6.5-7.191)
    * SLES 10 (2.6.16.21)
    * RHEL 3 UP7 (2.4.21-40)
    * RHEL 4 UP3 (2.6.9-34)
     * RHEL 4 UP4 (2.6.9-42)
    * Fedora Core 5 (2.6.15-1)
    * RHEL 4 UP2 (2.6.9-22)
    * RHEL 3 UP6 (2.4.21-37)
    * RHEL 3 UP8 (2.4.21-47)
    * SuSE 10 (2.6.13-15)

I downloaded the zip and every distro has it's own folder with it's own set of drivers. I'd rather not try this with every version.

Also included on the site:

Component 	Platform 	                Use this driver
Audio (AC97) 	nForce-1 – nForce-4 	intel8x0.c
Audio (HDA) 	nForce-430 and later 	hda_intel.c
 
Storage 	SATA 	                             sata_nv.c
                      ACHI 	                           ahci.c
                      IDE 	                             amd74xx.c
 
Ethernet 	All 	forcedeth.c

Any suggestions would be great, and if I can figure this out, I'll post my findings.

Thanks in advance!

---

### Post by vtel57 on 2007-05-23
Are you by any chance trying to install Ubuntu on a software RAID array?

---

