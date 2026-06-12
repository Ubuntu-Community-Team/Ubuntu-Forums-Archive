---
title: "core 2 duo cpu scaling"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by rymo on 2007-04-04
Hi guys.
I've installed ubuntu on asus f3jp notebook. 
What i've done with it:
-made kubuntu
-updated whole system (so newer kernel was installed)

The problem is that I can't scale the cpu frequency. The life time on battery is very short :(

I found some howto about enabling this option, but one said about searching the cpufreq directory (which i haven't got) the second one about installing linux-686-smp.. which i've done but with no effect :(

this is part of dmesg which is about cpu (i hope...)(17179687.220000) ACPI Error (psparse-0537): Method parse/execution failed (\_PR_.CPU1._PSS) (Node dffdca18), AE_AML_PACKAGE_LIMIT
(17179687.220000) ACPI Exception (acpi_processor-0240): AE_AML_PACKAGE_LIMIT, Evaluating _PSS (20060707)
(17179687.220000) ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFD) is beyond end of object (20060707)
(17179687.220000) ACPI Error (psparse-0537): Method parse/execution failed (\_PR_.CPU2._PSS) (Node dffdc860), AE_AML_PACKAGE_LIMIT
(17179687.220000) ACPI Exception (acpi_processor-0240): AE_AML_PACKAGE_LIMIT, Evaluating _PSS (20060707)

---

### Post by Bachstelze on 2007-04-04
First, you need to make sure relevent modules are installed, please paste the output of

```
lsmod | grep acpi[code]

and

[code]lsmod | grep cpu
```

---

### Post by rymo on 2007-04-04
```

lsmod | grep acpi
sony_acpi               6412  0 
pcc_acpi               14080  0 
dev_acpi               12292  0 
asus_acpi              17688  0 


lsmod | grep cpu
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 

```

---

### Post by rymo on 2007-04-07
any help?

---

### Post by Bachstelze on 2007-04-07
All right, we need some tools for this :

```
sudo apt-get install cpufrequtils cpufreqd
```

Then do

```
cpufreq-info
```

and paste what you get.

---

### Post by rymo on 2007-04-07
```
 
cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```

---

### Post by Bachstelze on 2007-04-07
Hmm, since Intel Core CPUs are relatively new, you might need to upgrade to Feisty to get a cpufreq driver for them. Maybe the one used on Pentium M's will work, try

```
sudo modprobe speedstep-centrino
```

---

### Post by rymo on 2007-04-07
I've got fatal error "no such device"

---

### Post by Bachstelze on 2007-04-07
You need to upgrade to a 2.6.20 kernel then. Either upgrade to Feisty or compile one from source on your Edgy.

---

### Post by rymo on 2007-04-07
Fine, I'll do it tommorow ..cause i've got about 2am :)
Thx for quick respond :)

---

### Post by rymo on 2007-04-08
I tried to upgrade the kernel...everything went fine...but kernel doesn't start :|
I used this howto: [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
Kernel..from kernel.org

well... no i think i will try to upgrade to Feisty :)

---

### Post by rymo on 2007-04-12
I managed to install ubuntu 7.04..with new kernel. cpufreq-info has the same answer.

```

 lsmod | grep acpi
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi


```

grep cpu does not return any info (strange...one reboot before it did :( )

---

### Post by Bachstelze on 2007-04-12
What happens when you do this ?

```
sudo modprobe acpi-cpufreq
```

If you get the same message as before ("no such device"), I don't think there's support for freq scaling in those CPUs yet.

---

### Post by rymo on 2007-04-12
Yeah..I get no such device :(

---

### Post by Bachstelze on 2007-04-12
Then now only thing you can do is see the changelog for every new version of the kernel and see if support for your CPU was added.

---

### Post by rko618 on 2007-06-11
rymo, did you ever get this working?

---

### Post by d34th on 2007-07-24
I have the same problem here, with an Intel Core 2 duo E6600, frequency scaling is enabled in the BIOS as long it works in windows, I'm using the default generic kernel (2.6.8.20-22 I think)
When i'm trying to load those modules i get "no such device", (it seems to be the wrong module)

---

### Post by mbrady on 2007-07-24
I'm using the latest kernel and every time I shut down, it gives me an error that CPU frequency scaling could not be enabled, explaining that a directory could not be created because a directory was not found... :\

I'll post more details when I get back home.

---

### Post by ACGarib on 2007-08-02
I have the same problem with one difference. I had CPU scaling working, but after a reboot, it put my core 2 duo T7300 processor in 800 MHz mode and it would not scale back up. I rebooted again and it says CPU frequency scaling is unsupported. Its been like that ever since.

If I reboot from terminal, I get: "Starting CPU frequency daemon cpufreqd    [fail]" as it is powering down.

---

### Post by daverich on 2007-08-06
I have this problem too.

Just started today - it was working fine until today.

Kind regards

Dave Rich

---

### Post by daverich on 2007-08-06
I found a script somewhere on this forum about putting a sleep command in the powernowd file.

That worked.

Turns out the script was running before the computer was ready for it.

Kind regards

Dave Rich

---

### Post by d3v1us on 2007-10-11
that would require having powernowd installed.

i don't have it installed and am wondering if you can make cpufreqd work for a core 2 duo system without powernowd.  has this problem with cpufreqd really not been resolved?

---

### Post by kripkenstein on 2008-06-19
I am having this problem with a new Core 2 Duo... as the previous poster asked a long time ago, has this never been solved? Are all Core 2 Duos not using frequency scaling? :(

---

