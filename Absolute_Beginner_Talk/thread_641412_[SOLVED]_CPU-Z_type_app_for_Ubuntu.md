---
title: "[SOLVED] CPU-Z type app for Ubuntu?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-12-15
Is there a [CPU-Z](http://www.cpuid.com/cpuz.php) type app or term command to find out what the main board (motherboard) is w/out having to crack open my case?

I know I could run [CPU-Z](http://www.cpuid.com/cpuz.php) in WINE but I am looking for an Ubuntu alternative.

---

### Post by Krydahl on 2007-12-15
You don't need the terminal: System -> Preferences -> Hardware Information

---

### Post by BassKozz on 2007-12-15
> **Krydahl said:**
> You don't need the terminal: System -> Preferences -> Hardware Information
I am using Xubuntu (probably should've mentioned that), I don't have a "Preferences" section under System.

---

### Post by Krydahl on 2007-12-15
OK type "lshw" at the terminal.

---

### Post by BassKozz on 2007-12-15
> **Krydahl said:**
> OK type "lshw" at the terminal.

Did that but it's not giving me the mainboard (motherboard) model number :(
**RESULTS**:```
lshw
WARNING: you should run this program as super-user.
User
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

```

---

### Post by Krydahl on 2007-12-15
Oops, so it isn't.

Hmm [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634729](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634729)

looks good.

---

### Post by arvevans on 2007-12-15
"sudo lshw" or any other way to execute the "lshw" at root/super-user level should show the decoded motherboard product ID.

Arv
_._

[INDENT]arv@arv-desktop:~$ sudo lshw
[sudo] password for arv:
arv-desktop               
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-7139
       physical id: 0
       version: 2.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/11/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.2
          slot: Socket 939
          size: 2GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
        *-cache:0
[/INDENT]

---

### Post by logos34 on 2007-12-15
sudo lshw -C CPU
sudo lshw -C memory
cat /proc/cpuinfo
cat /proc/meminfo

those four commands should cover just about everything reported by cpu-z

---

### Post by BassKozz on 2007-12-15
> **Krydahl said:**
> Oops, so it isn't.

Hmm [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634729](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634729)

looks good.
```
sudo dmidecode | more
``` WORKS !!! :)
THANKS :D

---

### Post by BassKozz on 2007-12-15
> **arvevans said:**
> "sudo lshw" or any other way to execute the "lshw" at root/super-user level should show the decoded motherboard product ID.

Arv
_._

[INDENT]arv@arv-desktop:~$ sudo lshw
[sudo] password for arv:
arv-desktop               
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-7139
       physical id: 0
       version: 2.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/11/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.2
          slot: Socket 939
          size: 2GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
        *-cache:0
[/INDENT]
Ahh, sudo did the trick also
> **logos34 said:**
> sudo lshw -C CPU
sudo lshw -C memory
cat /proc/cpuinfo
cat /proc/meminfo

those four commands should cover just about everything reported by cpu-z
Great thanks for the info...


THANKS for the help everyone :)

---

