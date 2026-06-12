---
title: "FATAL: Error inserting speedstep_centrino"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-04-22
hi.
i'd like to set-up processor scaling. i'm using feisty
i've got core 2 duo processor, and i followed this howto

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

(it's for edgy, i couldn't find this information in feisty howto :-/)

during step:

 sudo modprobe speedstep-centrino 

i get an error :

FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

my uname -r

2.6.20-15-generic

it's 'standard' kernel (i.e: it's not my own compilation)

---

### Post by Bachstelze on 2007-04-22
Core CPU's are _not_ Centrinos, they are not supported by the speedstep-centrino module.

---

### Post by szymon_g on 2007-04-22
ok, i solved problem :P
i shouldn't use speedstep_centrino modul on feisty's kernel (but it used to work on edgy :o).
i should use acpi_cpufreq :P

---

### Post by cb474 on 2007-08-12
> **HymnToLife said:**
> Core CPU's are _not_ Centrinos, they are not supported by the speedstep-centrino module.

Huh? But in the Feisty User Guide ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)) it specifically says that the speedstep-centrino module is for Core Duo processors.

In Edgy it installed and worked fine for me (I'm on a ThinkPad T60). But in Feisty I get the same "No Such Device" error message. Also, in my BIOS it specifically says it's using SpeedStep.

---

### Post by Bachstelze on 2007-08-12
```
lsmod | grep acpi
```

If *acpi-cpufreq* is already loaded, then you don't need *speedstep-centrino*, *acpi-cpufreq* replaced it in kernel 2.6.18.2.

---

