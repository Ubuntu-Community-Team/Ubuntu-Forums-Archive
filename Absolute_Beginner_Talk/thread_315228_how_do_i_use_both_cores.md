---
title: "how do i use both cores?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2006-12-08
Hi, I just finished putting together my new pc with an amd 165 opteron dual core processor. How do i go about installing dual core support? 
I am using kubuntu edgy on this box, with the x86 regualar installation. thanks!

---

### Post by taurus on 2006-12-08
What's the output of this command from a terminal?

```
cat /proc/cpuinfo
```

---

### Post by Tezcatlipoca on 2006-12-08
> **jeffc313 said:**
> Hi, I just finished putting together my new pc with an amd 165 opteron dual core processor. How do i go about installing dual core support? 
I am using kubuntu edgy on this box, with the x86 regualar installation. thanks!


Edgy's default "Generic" kernel should support dual cores without you needing to do anything AFAIK.

---

### Post by %hMa@?b&lt;C on 2006-12-08
> **taurus said:**
> What's the output of this command from a terminal?

```
cat /proc/cpuinfo
```
i will reboot and show the "generic" kernel but that one specifically says 
cores : 1
```
crowell@opteron:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 1809.457
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 3622.52

```
```
crowell@opteron:~$ uname -r
2.6.17-10-386

```

---

### Post by scxtt on 2006-12-08
you should have to install an *-smp kernel to get support for both CPUs ...

---

### Post by %hMa@?b&lt;C on 2006-12-08
> **scxtt said:**
> you should have to install an *-smp kernel to get support for both CPUs ...
```
crowell@opteron:~$ uname -r
2.6.17-10-generic
crowell@opteron:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 1809.410
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 3622.70

```
i didi install linux-686-smp or something

---

### Post by scxtt on 2006-12-08
you don't have a x86 processor ... try installing what i've highlighted in red ...```
[font=courier]:> aptitude search smp
p   alamin-smpp                                         - Alamin GSM SMS Gateway SMPP interface
p   kernel-headers-2.4.27-2-686-smp                     - Linux 2.4.27 kernel headers for PPro/Celeron/PII/PIII/P4 SMP
p   kernel-headers-2.4.27-2-k7-smp                      - Linux 2.4.27 kernel headers for AMD K7 SMP
p   kernel-image-2.4.27-2-686-smp                       - Linux kernel image for version 2.4.27 on PPro/Celeron/PII/PIII
p   kernel-image-2.4.27-2-k7-smp                        - Linux kernel image for version 2.4.27 on AMD K7 SMP
p   kernel-pcmcia-modules-2.4.27-2-686-smp              - Mainstream PCMCIA modules 2.4.27 on PPro/Celeron/PII/PIII/P4 S
p   kernel-pcmcia-modules-2.4.27-2-k7-smp               - Mainstream PCMCIA modules 2.4.27 on AMD K7 SMP
p   libnet-smpp-perl                                    - Net::SMPP is an implementation of Short Message Peer to Peer p
p   libsmpeg-dev                                        - SDL MPEG Player Library - development files
p   libsmpeg0                                           - SDL MPEG Player Library - shared libraries
v   libsmpeg0c2                                         -
p   linux-686-smp                                       - Complete Linux kernel on PPro/Celeron/PII/PIII/PIV SMP.
[color=red]**p   linux-k7-smp                                        - Complete Linux kernel on AMD K7 SMP.**[/color]
p   pcmcia-modules-2.4.27-2-686-smp                     - PCMCIA Modules for Linux (kernel 2.4.27-2-686-smp)
p   pcmcia-modules-2.4.27-2-k7-smp                      - PCMCIA Modules for Linux (kernel 2.4.27-2-k7-smp)
p   smpeg-gtv                                           - SMPEG GTK+ MPEG audio/video player
p   smpeg-plaympeg                                      - SMPEG command line MPEG audio/video player
p   smpeg-xmms                                          - SDL MPEG Player Library - XMMS plugin
i   smproxy                                             - X client - smproxy
p   ssmping                                             - check your multicast connectivity
p   wmsmpmon                                            - A CPU monitoring dockapp for SMP systems

:> aptitude show linux-k7-smp
Package: linux-k7-smp
State: not installed
Version: 2.6.15.25
Priority: optional
Section: restricted/base
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 53.2k
Depends: linux-image-k7, linux-restricted-modules-k7
Description: Complete Linux kernel on AMD K7 SMP.
 This package will always depend on the latest complete Linux kernel available for AMD Duron/Athlon with SMP support.
 SMP (symmetric multi-processing) is needed if you have multiple processors.[/font]
```

---

### Post by %hMa@?b&lt;C on 2006-12-10
had to reflash my bios. now dual core works, but the opteron is reporting 1,000 MHz insead of 1,800 MHz in both cores. any ideas?
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2012.60

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2012.60

crowell@opteron:~$ uname -a
Linux opteron 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```

---

### Post by kinematic on 2006-12-10
that's probably the cpu scaling doing it's work.
in the output you posted you can see that's it's a stepping 2 cpu wich means that it can be scaled to 2 frequencys(1800 mhz and 1000 mhz).
when you don't need processing power the powernow daemon scales it down to 1000 mhz to save on power consumption....when you do need extra oumph it goes to full power on the fly.
if you rightclick on empty space in the in the gnome panel you can add the cpu applet wich let's you see it in real time.

---

### Post by blueCommand on 2006-12-10
Quoting Wikipedia:

"Stepping is a designation used by Intel and AMD to identify how much the design of a microprocessor has advanced from the original design. The stepping is identified by a combination of a letter and a number."

I always thought stepping was a version number, not how much it clocks down :\.
But never the less, it sounds like the PowerNow function.

---

### Post by Frank Golden on 2006-12-10
> **kinematic said:**
> that's probably the cpu scaling doing it's work.
in the output you posted you can see that's it's a stepping 2 cpu wich means that it can be scaled to 2 frequencys(1800 mhz and 1000 mhz).
when you don't need processing power the powernow daemon scales it down to 1000 mhz to save on power consumption....when you do need extra oumph it goes to full power on the fly.
if you rightclick on empty space in the in the gnome panel you can add the cpu applet wich let's you see it in real time.
Hi all,
   He's using kubuntu, no Gnome applet. Don't know if kde in Edgy
has a similar applet. It does in PCLinuxOS. If you find a similar
tool in kubuntu make two and set up one for each proc core.
In Gnome all I had to do was right click each and choose properties and use the Cpu dropdown box. In Gnome there is a hack to allow the user to change the settings of these applets.
For instance user could set up proc to run at full throttle all the time.

---

### Post by kinematic on 2006-12-10
i thought that it refered to the scaling.....guess it doesn't ;)

---

### Post by Frank Golden on 2006-12-10
> **kinematic said:**
> i thought that it refered to the scaling.....guess it doesn't ;)
The Gnome applet does show the scaling in real time. The one kde uses
in PCLinuxOS does also.
Using the hack you have more control.

"and as suggested in it, I did a
$ sudo dpkg-reconfigure gnome-applets
and answered “Yes” to the question regarding setting the suid of the cpufreq-selector executable. Now, by left-clicking on the CPU Frequency Monitor Applet, I can choose the frequency for my processor, and things couldn’t be better!!"

See this link for source of above info.
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by %hMa@?b&lt;C on 2006-12-10
thanks for the info, i just tested during a benchmarking test and it was running at full speed thanks!

---

### Post by RockoTDF on 2006-12-10
> **jeffc313 said:**
> thanks for the info, i just tested during a benchmarking test and it was running at full speed thanks!

If it gives you any more problems in this area, check the bios to make sure the FSB is at full speed.  Back when I had an athlon xp and had to flash the bios, it turns down the FSB and made the computer think it was a 1500 instead of a 2100.

---

