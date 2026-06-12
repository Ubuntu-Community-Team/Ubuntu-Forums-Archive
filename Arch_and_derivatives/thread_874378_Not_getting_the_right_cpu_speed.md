---
title: "Not getting the right cpu speed"
date: 2008-07-29
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-07-29
I felt ambitious today and bumped my q6600 to 3.6ghz (9x400). Arch still sees this as it's stock 2.4Ghz and was wondering why it would. It was working earlier today.

cpufreq-info
```

cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1 2 3
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: ondemand, performance
  current policy: frequency should be within 1.60 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1 2 3
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: ondemand, performance
  current policy: frequency should be within 1.60 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz.
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1 2 3
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: ondemand, performance
  current policy: frequency should be within 1.60 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz.
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1 2 3
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: ondemand, performance
  current policy: frequency should be within 1.60 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz.

```

cat /proc/cpuinfo

```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
cpu MHz        : 2394.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips    : 7214.96
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
cpu MHz        : 2394.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips    : 12816.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
cpu MHz        : 2394.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips    : 7210.14
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
cpu MHz        : 2394.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips    : 7210.13
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by cardinals_fan on 2008-07-29
I don't know, but I'm jealous of that CPU :)

---

### Post by PurposeOfReason on 2008-07-29
> **cardinals_fan said:**
> I don't know, but I'm jealous of that CPU :)
Why thank you. I have a bigger concern now. When I boot no modules load. A big fail on the boot screen of module not found so I can't do anything as not even a keyboard works. I honestly think I might have to reinstall.

---

### Post by cardinals_fan on 2008-07-29
> **PurposeOfReason said:**
> Why thank you. I have a bigger concern now. When I boot no modules load. A big fail on the boot screen of module not found so I can't do anything as not even a keyboard works. I honestly think I might have to reinstall.
Arch is a pretty easy distro to reinstall.  Just pop in the CD, reboot, install, upgrade, pacman -S your needed packages, and perform a little configuration.

---

### Post by PurposeOfReason on 2008-07-29
> **cardinals_fan said:**
> Arch is a pretty easy distro to reinstall.  Just pop in the CD, reboot, install, upgrade, pacman -S your needed packages, and perform a little configuration.
It's a brand new install though, I just did it. Anyways, depmod -a is supposed to fix it. I have a keyboard if I boot into the existing system through the CD, but then it's the wrong kernel and it won't work so if somebody knows how to tell depmod to use x kernel location, I'd love it.

Also, a max connection of 150kbs and wanting gnome takes a while. ;)

EDIT - Reinstalled kernel26 through pacman and we're back in business. It looks like acpi-cpufreq is stopping the overclock

---

### Post by cardinals_fan on 2008-07-29
> **PurposeOfReason said:**
> It's a brand new install though, I just did it. Anyways, depmod -a is supposed to fix it. I have a keyboard if I boot into the existing system through the CD, but then it's the wrong kernel and it won't work so if somebody knows how to tell depmod to use x kernel location, I'd love it.

Also, a max connection of 150kbs and wanting gnome takes a while. ;)
I feel your pain.  You could use Openbox instead... :)

---

### Post by kool_kat_os on 2008-07-29
i hear that there is a great distro out there....oh...whats its name?.....oh ya....ubuntu :-D

---

### Post by cardinals_fan on 2008-07-30
> **kool_kat_os said:**
> i hear that there is a great distro out there....oh...whats its name?.....oh ya....ubuntu :-D
Arch is rolling release, built from the command line up, and KISS.  Ubuntu has a 6-month release cycle, includes a fairly bloated GUI, and handles most configuration out of the user's sight.  The two distros have pretty different target audiences, wouldn't you say?

---

### Post by PurposeOfReason on 2008-07-30
> **cardinals_fan said:**
> I feel your pain.  You could use Openbox instead... :)
It's my delima. I love openbox. If you look in the openbox screenshot thread on the arch forums you see why, pipe menus. I just feel like I'd be wasting so much power so my compromise is arch is gnome + compiz. I'm also going to do gentoo with openbox and xcompmgr and then bsd + something. Not too sure yet. Each has it's own benefits which is why I want all three.

---

### Post by mips on 2008-07-30
> **PurposeOfReason said:**
> It's a brand new install though, I just did it. Anyways, depmod -a is supposed to fix it. I have a keyboard if I boot into the existing system through the CD, but then it's the wrong kernel and it won't work so if somebody knows how to tell depmod to use x kernel location, I'd love it.

Also, a max connection of 150kbs and wanting gnome takes a while. ;)

EDIT - Reinstalled kernel26 through pacman and we're back in business. It looks like acpi-cpufreq is stopping the overclock

Did you install cpufrequtils and reconfigure the frequency range? Stock it would be 1.6GHz-2.4GHz, so you would have to bump the 2.4GHz up to 3.6GHz

I have the same cpu but have not tried overclocking it yet. Are you using any special heatsinks/coolers and what temperaure does it run at when overclocked?

---

### Post by Dr Small on 2008-07-30
> **cardinals_fan said:**
> Arch is rolling release, built from the command line up, and KISS.  Ubuntu has a 6-month release cycle, includes a fairly bloated GUI, and handles most configuration out of the user's sight.  The two distros have pretty different target audiences, wouldn't you say?
What a beautiful explanation :D

---

### Post by cardinals_fan on 2008-07-30
> **Dr Small said:**
> What a beautiful explanation :D
Thank you :)

---

### Post by PurposeOfReason on 2008-07-30
> **mips said:**
> Did you install cpufrequtils and reconfigure the frequency range? Stock it would be 1.6GHz-2.4GHz, so you would have to bump the 2.4GHz up to 3.6GHz

I have the same cpu but have not tried overclocking it yet. Are you using any special heatsinks/coolers and what temperaure does it run at when overclocked?
It's watercooled so the main temp is 23 and the cores run 39/42/41/38. Load goes to 30 59/63/64/62. You can do a basic overclock to 3.Ghz just bumping the FBS to 333 and wouldn't have to touch anything else. Most people do that on air and get temps like I just posted.

It's confirmed though, right when I modprobe acpi-cpufreq it stops the overclock. Here is the /etc/conf.d/cpufreq
```

#configuration for cpufreq control

# valid governors:
#  ondemand, performance, powersave,
#  conservative, userspace
governor="ondemand"

# valid suffixes: Hz, kHz (default), MHz, GHz, THz
min_freq="1.60GHz"
max_freq="3.6GHz"

```

---

### Post by PurposeOfReason on 2008-08-02
Took the fresh install advice which I didn't think would work, and it didn't. I'm beginning to think it's looking in my BIOS for something I probably have disabled.

---

### Post by geekygirl on 2008-08-07
> **PurposeOfReason said:**
> It's watercooled so the main temp is 23 and the cores run 39/42/41/38. Load goes to 30 59/63/64/62. You can do a basic overclock to 3.Ghz just bumping the FBS to 333 and wouldn't have to touch anything else. Most people do that on air and get temps like I just posted.

It's confirmed though, right when I modprobe acpi-cpufreq it stops the overclock. Here is the /etc/conf.d/cpufreq
```

#configuration for cpufreq control

# valid governors:
#  ondemand, performance, powersave,
#  conservative, userspace
governor="ondemand"

# valid suffixes: Hz, kHz (default), MHz, GHz, THz
min_freq="1.60GHz"
max_freq="3.6GHz"

```

Are you saying that it is adjusting a BIOS overclock through the software itself?

what did ```
dmesg | grep proc 
```say?


I would have thought adjusting the range of the ACPI table would give a different result as it seems to be a reporting issue?

Anyone else with some more idea's? With an overclocked CPU I am interested in how a BIOS overclock can be adjusted via the operating system, or is it just a reporting issue as the ACPI modules have not been written to allow for changes in the range of frequencies the CPU can operate at.

This also seems to be a common issue for CPU overclocking under Linux :(

---

