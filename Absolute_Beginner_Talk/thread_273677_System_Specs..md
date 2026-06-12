---
title: "System Specs."
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-10-08
Hey, really newbie question here, I've just installed some new RAM and just want to check that its been installed ok, is there a way of checking what your system specs are via the terminal? Thanks

---

### Post by Lord Illidan on 2006-10-08
```
cat /proc/meminfo
```

---

### Post by rfruth on 2006-10-08
The lshw command will do it - here's mine
[http://www.rfruth.net/resume/computers/breezy/breezylshw.txt](http://www.rfruth.net/resume/computers/breezy/breezylshw.txt)

---

### Post by Lord Illidan on 2006-10-08
Nice one mate, didn't know about that one!

---

### Post by Olly1234 on 2006-10-08
Cheers!

---

### Post by chalex on 2006-10-08
Alternatively, ```
free -m
```.

The program "free" merely reformats the output for "/proc/meminfo" to be easier to read.  The -m switch displays the results in MB.

---

### Post by JayTee on 2006-10-08
When I run the lshw command I get the following output from my Pentium D 940 3.2GHZ cpu. It says 2400mhz for both CPUs. Is this normal? Is it a stepping thing?
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2023MB
     *-cpu:0
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical

---

