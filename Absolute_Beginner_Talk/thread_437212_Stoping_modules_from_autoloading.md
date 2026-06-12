---
title: "Stoping modules from autoloading"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-05-08
How can I tell ubuntu not to load some modules during boot? I want to replace acpi_cpufreq module with speedstep-centrino that better suits my computer, but ubuntu loads acpi_cpufreq during boot and I can not remove it, as it is used. I've tried putting acpi_cpugreq in /etc/modprobe.d/blacklist but it still loads.

---

### Post by Timo425 on 2007-05-08
........

Sorry, my bad, this is different.

---

### Post by ggaaron on 2007-05-08
No, I can not:

my /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse

```

and lsmod has a lot longer list.

---

