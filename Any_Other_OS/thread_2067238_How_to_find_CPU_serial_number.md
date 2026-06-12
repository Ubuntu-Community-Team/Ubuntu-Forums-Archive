---
title: "How to find CPU serial number"
date: 2012-10-06
forum: Any Other OS
---

### Post by tech291083 on 2012-10-06
Hi,
 
I am using win 7 Home Basic 64+ bit OS. I do not want to dismantle the pc and check the serial number of the cpu. Is there a tool that can do so? Thanks.

---

### Post by Lars Noodén on 2012-10-06
You could boot a live CD and then run [lshw](http://manpages.ubuntu.com/manpages/precise/en/man1/lshw.1.html) to see if that gives you the right information.

```

sudo lshw -class processor

```

---

### Post by drmrgd on 2012-10-06
That's a cool trick.  Didn't know you could find the serial number with that.  Well sort of...mine's funny:

```
*-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
       serial: To Be Filled By O.E.M.
       slot: LGA2011
       size: 1200MHz
       capacity: 4GHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=6 enabledcores=6 threads=12
```

Since I built it, I guess I'm the OEM.  Now I have to think of a serial number, I guess....

---

### Post by tech291083 on 2012-10-07
> **Lars Noodén said:**
> You could boot a live CD and then run [lshw]("http://manpages.ubuntu.com/manpages/precise/en/man1/lshw.1.html") to see if that gives you the right information.
 
```

sudo lshw -class processor

```
 
Thanks for the reply. But I am a little confused here. Are you talking about Win 7 live CD? If yes, then I do not have one with me. If you are talking about a live CD of some Linux distro then I migh have one using which I can do the command you have talked about. I only have Win 7 installed on this HDD and no other OS. Thanks.

Hi,
 
Jus wondering if there are other commands to know the serial numbers of other parts in a pc namely HDD, motherboard, RAM etc. This can be really helpful when you do not have the sales receipt. Thanks.

---

### Post by mips on 2012-10-07
You can try one of the many system infor utilities in windows.
These are all freeware [http://www.techsupportalert.com/best-free-system-information-utility.htm](http://www.techsupportalert.com/best-free-system-information-utility.htm)

As for the CPU serial number that info might not be available to you. Post PIII cpu many manufacturers disabled this in the cpu or BIOS.
[http://en.wikipedia.org/wiki/CPUID#EAX.3D3:_Processor_Serial_Number](http://en.wikipedia.org/wiki/CPUID#EAX.3D3:_Processor_Serial_Number)

---

### Post by Lars Noodén on 2012-10-07
> **tech291083 said:**
> ...If you are talking about a live CD of some Linux distro then I migh have one using which I can do the command you have talked about...

Yes, I was thinking in particular one of the Ubuntu Desktop (live) CDs.  Other Linux distros have live CDs that might also be of use.  There is no need to install, yet, just run the Live session.

---

