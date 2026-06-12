---
title: "Issuer with &quot;Old World Intel Mac&quot; Graphics Support after 20.04 to 21.04 upgrade"
date: 2021-06-18
forum: Apple Hardware Users
---

### Post by freddofrog2 on 2021-06-18
Hi Folks,

I need to report an issue that I have observed when going through an upgrade from 10.04, to 20.10 (no issues observed here) but the 21.04 upgrade reports that the Radeon controller is unclaimed, and resolutions are locked at 1400 x 1050 when the correct screen resolution should be  1680 x 1050.

i.e. root@Old-iMac:/home/freddof# lshw -c video  *-display UNCLAIMED   <== <== <== THE MAIN ISSUE
       description: VGA compatible controller
       product: RV530/M56-P [Mobility Radeon X1600]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff ioport:2000(size=256) memory:d0400000-d040ffff memory:c0000-dffff

The only way that a non-corrupted login screen (at 1400 x 1050) can be obtained is by setting "nomodeset" in the GRUB2 Configration file.

There are still many of us that use Ubunto on "Old-World" macs. The 21.04 release is important as it is the only Ubuntu release that delivers Qt 5.15.2 support.

Does anyone have any suggestions on a short-term fix?

Yet I believe that patches to make this work may be in order - even for this old hardware - for some time.

Regards,

Freddo

---

### Post by freddofrog2 on 2021-06-18
Supplemental: I am aware of this: [https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by jeremy31 on 2021-06-18
Moved to Apple hardware

---

