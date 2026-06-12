---
title: "intel hd audio problem on media center pc"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Burberry on 2008-02-05
I have a Philips Media Center MCP9350i, which I am trying to port over to Linux. My intent is to run MythTV to view TV. I have installed Kubuntu 7.04 and upgraded it to 7.10. Before I can tackle the issues of getting the video capture card working, etc. I need to try and get the sound working.

It seems to find the card, but for some reason it just wont work. Could anyone help me perhaps?

Including some information requested in other posts relating to audio problems. Let me know if you need more information. I have tried to do my homework, but still cant seem to get this working.

Could someone help me and point me in the right direction?

Audio card output from sudo lshw

```

        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Audio output from lspci -v 

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 071a
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 31240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

lspci

```

burb@burb:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:00.0 Multimedia controller: Unknown device 1745:2010
04:02.0 Ethernet controller: Atheros Communications, Inc. AR5413 802.11abg NIC (rev 01)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```

Motherboard and CPU output from sudo lshw

```

burb@burb:~$ sudo lshw
[sudo] password for burb:
burb
    description: Computer
    vendor: "Tatung co."
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=A49A5FAC-0741-11DA-9419-00E018EB0C94
  *-core
       description: Motherboard
       product: D945GSU
       vendor: Intel Corporation
       physical id: 0
       version: AAD19017-202
       serial: AZSU53200172
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          size: 3GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0

```

I can of course output the whole sudo lshw or alike if needed.

Pleeease help me! :)

---

### Post by wolfen69 on 2008-02-05
see this [http://ubuntuforums.org/showthread.php?t=314383&highlight=intel+hda](http://ubuntuforums.org/showthread.php?t=314383&highlight=intel+hda)

---

### Post by Burberry on 2008-02-05
Thanks for your feedback Wolfen69. I have previously seen this post, but there is nothing that says Philips there. I have tried both the sigmatel versions, because I have seen some reference to that in some of the print outs. However, nothing.

Any other ideas on how I found what to then enter in the alsa-base config?

---

