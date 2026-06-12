---
title: "Can I check the CPU/system temp in console?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by bashhelp on 2005-11-21
Can I check the CPU/system temperature in console?  If so, what is the command?

---

### Post by tokyovigilante on 2005-11-21
It depends on your architecture. If you have a relatively recent computer (last 3-4yrs) Try [ACPI4Linux]("http://acpi.sourceforge.net/documentation/thermal.html"), then navigate through the /proc/acpi directory structure. 
```
cat /proc/acpi/thermal_zone/temperature
``` will probably do what you want. More info may be available if your system supports more ACPI states (partic laptops).

---

### Post by az on 2005-11-21
install lm-sensors thorugh your favorite package management mechanism (synaptic, kynapti, apt-get, aptitude...whatever)

Open a terminal and run

sudo sensors-detect

and follow the instructions.

The run 
sensors (I can<t remember if you need to be root)

You may also install mbmon and run
sudo mbmon. Mbmon does not use a kernel module.

---

### Post by joshpelkey on 2005-11-22
The command "acpi -t" or "acpi -tf" may also work for ya.

---

### Post by bluevoodoo1 on 2005-11-22
[QUOTE=azz]install lm-sensors thorugh your favorite package management mechanism (synaptic, kynapti, apt-get, aptitude...whatever)

Open a terminal and run

sudo sensors-detect

and follow the instructions.

The run 
sensors (I can<t remember if you need to be root)
[/QUOTE]

I get to a part where it tells me to manually copy and paste some code... where do i copy it to and how do I go about doing that? (exact commands would be great)

---

### Post by Specialsauce on 2005-11-22
wow.... i didnt think that was possible 0_o

---

### Post by bluevoodoo1 on 2005-11-22
got it. It seems that it only checks my ram and not temps/speeds. Perhaps my hardware is too old? oh well.

---

