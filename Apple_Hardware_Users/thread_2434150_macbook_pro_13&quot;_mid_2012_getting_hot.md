---
title: "macbook pro 13&quot; mid 2012 getting hot"
date: 2019-12-31
forum: Apple Hardware Users
---

### Post by mohddxb on 2019-12-31
hello 
just install ubuntu. and my macbook very hot
i installed tlp , thermald , macfanctld but still macbook is hot 
```
&#10140;  ~ sensors            
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +63.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:        +61.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:        +63.0°C  (high = +87.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   3147 RPM  (min = 3150 RPM, max = 6200 RPM)
TA0P:         +46.0°C  
TB0T:         +35.5°C  
TB1T:         +35.5°C  
TB2T:         +34.0°C  
TC0E:         +61.8°C  
TC0F:         +63.8°C  
TC0J:          +1.8°C  
TC0P:         +56.2°C  
TC1C:         +61.0°C  
TC2C:         +69.0°C  
TCGC:         +61.0°C  
TCSA:         +61.0°C  
TCTD:          +0.0°C  
TCXC:         +63.2°C  
TG1D:         +63.8°C  
TM0P:         +43.5°C  
TM0S:         +52.8°C  
TPCD:         +71.0°C  
Th1H:         +50.8°C  
Ts0P:         +33.5°C  
Ts0S:         +43.8°C  

&#10140;  ~ 


```
please help me 
thanks

---

### Post by jbod43 on 2019-12-31
have you tried dusting out the holes where the exhaust vents are?  they are in the crease between the screen and the rest of the body on the lower part.  They are revealed by opening the screen to the furthest position.  Get yourself a can of PC duster, and clear those holes out.  Just be careful not to spray the liquid in there.   The can works best if it is held straight up and down, so hold the laptop in the awkward position necessary so have the can straight up and down.  When the can spits out too much when tilted, or if it just gets too cold from too much spraying too much in too little time, it will start to spit out liquid.   So little short blasts with the can upright, and you should get just air.Note, flipping the can upside down will spray out straight liquid.  Do not do this!I understand that many have sprayed their motherboard with liquid with no ill effects, but this is the inside of your expensive laptop.  Be careful with her!

---

### Post by mohddxb on 2020-01-02
> **jbod43 said:**
> have you tried dusting out the holes where the exhaust vents are?  they are in the crease between the screen and the rest of the body on the lower part.  They are revealed by opening the screen to the furthest position.  Get yourself a can of PC duster, and clear those holes out.  Just be careful not to spray the liquid in there.   The can works best if it is held straight up and down, so hold the laptop in the awkward position necessary so have the can straight up and down.  When the can spits out too much when tilted, or if it just gets too cold from too much spraying too much in too little time, it will start to spit out liquid.   So little short blasts with the can upright, and you should get just air.Note, flipping the can upside down will spray out straight liquid.  Do not do this!I understand that many have sprayed their motherboard with liquid with no ill effects, but this is the inside of your expensive laptop.  Be careful with her!
Laptop is clean. When i log in with mac os laptop is working normal but when i log in with Ubuntu getting overheating 
several distro i try kubuntu, opensuse, Fedora kde, mint, fedora xfce, Ubuntu genom, manjaro
all same getting overheating 
thanks

---

### Post by Doug S on 2020-01-03
Which processor? Example:
```
doug@s15:~/c$ grep "model name" /proc/cpuinfo
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
...

```Which CPU scaling driver and governor? Example:

```
doug@s15:~/c$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_cpufreq
intel_cpufreq
...
doug@s15:~/c$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
schedutil
schedutil
...

```

---

### Post by mohddxb on 2020-01-03
```
$ grep "model name" /proc/cpuinfo
model name    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz

```

```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq

```

```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand

```

Thanks

---

### Post by Doug S on 2020-01-03
Suggest this command as a monitoring tool:
```
sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15
```
where turbostat is in the linux-tools-common package.
You can limit the CPU frequency to reduce heat. As a test (using 70% as an example):
```
echo 70 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```
Note: Depending on kernel version. There was a recent issue where, under certain conditions, max_perf_pct wasn't taking effect. I do not know if the fix has been backported.
Also Check "/sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq" as the two interact.

---

### Post by mohddxb on 2020-01-04
> **Doug S said:**
> Suggest this command as a monitoring tool:
```
sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15
```
where turbostat is in the linux-tools-common package.
You can limit the CPU frequency to reduce heat. As a test (using 70% as an example):
```
echo 70 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```
Note: Depending on kernel version. There was a recent issue where, under certain conditions, max_perf_pct wasn't taking effect. I do not know if the fix has been backported.
Also Check "/sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq" as the two interact.

```
 &#10140;  ~ sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15
turbostat version 18.07.27 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 0xd CPUID levels; 0x80000008 xlevels; family:model:stepping 0x6:3a:9 (6:58:9)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM HT TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, No-EPB
cpu1: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST MWAIT PREFETCH TURBO)
CPUID(7): No-SGX
cpu1: MSR_MISC_PWR_MGMT: 0x00400000 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 1872 sec. Joule Counter Range, at 35 Watts
cpu1: MSR_PLATFORM_INFO: 0x80c10e0011900
12 * 100.0 = 1200.0 MHz max efficiency frequency
25 * 100.0 = 2500.0 MHz base frequency
cpu1: MSR_IA32_POWER_CTL: 0x00300045 (C1E auto-promotion: DISabled)
cpu1: MSR_TURBO_RATIO_LIMIT: 0x1d1d1d1f
29 * 100.0 = 2900.0 MHz max turbo 4 active cores
29 * 100.0 = 2900.0 MHz max turbo 3 active cores
29 * 100.0 = 2900.0 MHz max turbo 2 active cores
31 * 100.0 = 3100.0 MHz max turbo 1 active cores
cpu1: MSR_CONFIG_TDP_NOMINAL: 0x00000019 (base_ratio=25)
cpu1: MSR_CONFIG_TDP_LEVEL_1: 0xc0000000000000 (PKG_MIN_PWR_LVL1=192 PKG_MAX_PWR_LVL1=0 LVL1_RATIO=0 PKG_TDP_LVL1=0)
cpu1: MSR_CONFIG_TDP_LEVEL_2: 0xc0000000000000 (PKG_MIN_PWR_LVL2=192 PKG_MAX_PWR_LVL2=0 LVL2_RATIO=0 PKG_TDP_LVL2=0)
cpu1: MSR_CONFIG_TDP_CONTROL: 0x80000000 ( lock=1)
cpu1: MSR_TURBO_ACTIVATION_RATIO: 0x00000000 (MAX_NON_TURBO_RATIO=0 lock=0)
cpu1: MSR_PKG_CST_CONFIG_CONTROL: 0x00000404 (UNlocked, pkg-cstate-limit=4 (pc7))
cpu1: cpufreq driver: intel_cpufreq
cpu1: cpufreq governor: ondemand
cpufreq intel_pstate no_turbo: 0
cpu1: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x10000000c00118 (35 W TDP, RAPL 24 - 0 W, 0.015625 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x3e800148320 (UNlocked)
cpu0: PKG Limit #1: ENabled (100.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (125.000000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00691200 (105 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x882a0000 (63 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (105 C, 105 C)
cpu1: MSR_PKGC3_IRTL: 0x00008894 (valid, 151552 ns)
cpu1: MSR_PKGC6_IRTL: 0x000088a9 (valid, 173056 ns)
cpu1: MSR_PKGC7_IRTL: 0x000088c6 (valid, 202752 ns)
Busy%    Bzy_MHz    IRQ    PkgTmp    PkgWatt    GFXWatt
1.64    1452    4108    59    3.89    0.16
2.29    1440    5360    62    4.28    0.36
10.19    1575    21191    64    6.60    1.38
6.95    1582    14941    62    5.52    0.82
11.97    1692    24955    63    6.63    1.30
6.69    1585    19710    63    5.18    0.55
17.63    1988    34259    64    6.64    1.03
10.61    1860    42954    60    5.75    0.74
4.36    1747    9439    62    4.65    0.41
4.22    1541    10183    60    5.28    0.88
4.90    1606    10184    62    5.25    0.79
15.46    1867    36455    65    6.99    1.29
15.06    1829    35641    66    7.03    1.34
2.47    1415    5773    60    4.14    0.26
3.13    1456    7143    62    4.21    0.21
9.06    1723    18235    62    5.78    0.85
4.05    1350    12909    62    5.34    0.93
3.54    1360    10804    60    4.92    0.67
5.39    1453    13431    64    5.52    0.88
10.20    1708    22150    64    6.56    1.34
11.91    1597    23303    65    7.20    1.67
8.82    1494    18314    63    6.05    0.99
9.52    1584    16901    64    6.50    1.32
7.53    1465    14857    64    6.40    1.41
5.81    1378    10936    64    6.18    1.39
6.31    1488    11389    64    6.23    1.39
9.18    1555    17506    64    6.68    1.48




```

```
echo 70 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```
i changed to 70 but still minimum 62C 

```
 sudo cat "/sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq"
cat: '/sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq': No such file or directory
```

```
&#10140;  ~ sudo cat "/sys/devices/system/cpu/cpufreq/policy0/scaling_max_freq"
3100000


```
Thsnks for you help

---

### Post by Doug S on 2020-01-04
Everything looks O.K. to me. The processor does seem a little warm for the load, but I don't think that is uncommon for laptops, not sure.
I put some small CPU load on my test server (not a LapTop) and got (minimum freq is 1600 MHz):

```
doug@s15:~/iso/prime95$ [COLOR="#FF0000"]sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15[/COLOR]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt
16.52   1600    29989   37      9.07    0.12
16.45   1600    29759   37      9.07    0.12
16.41   1600    29708   38      9.07    0.12
16.41   1601    29796   39      9.08    0.12
16.39   1601    29642   38      9.09    0.12
16.41   1600    29645   38      9.09    0.12
16.40   1600    29609   38      9.11    0.12
16.41   1600    29619   37      9.09    0.12
16.41   1602    29648   38      9.10    0.12
16.41   1600    29715   38      9.10    0.12
16.40   1600    29560   39      9.11    0.12
16.40   1600    29576   38      9.11    0.12

```Reducing the maximum CPU frequency had no effect because your CPU frequency was never hitting 70% anyhow. I was thinking of a more CPU heavy load scenario. Example:
```
doug@s15:~/iso/prime95$ [COLOR="#FF0000"]sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15[/COLOR]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt
100.00  3500    122398  79      63.73   0.12
100.00  3500    122321  80      63.92   0.12
100.00  3500    122367  79      63.99   0.12
100.00  3500    122414  79      64.10   0.12
100.00  3500    122402  79      64.14   0.12
100.00  3284    122481  73      58.72   0.12  [COLOR="#FF0000"]<<< Max to 70%[/COLOR] 
100.00  2700    122412  71      43.77   0.12
100.00  2700    122470  70      43.55   0.12
100.00  2700    122388  69      43.43   0.12
100.00  2700    122384  68      43.37   0.12
100.00  2700    122542  68      43.31   0.12

```

---

