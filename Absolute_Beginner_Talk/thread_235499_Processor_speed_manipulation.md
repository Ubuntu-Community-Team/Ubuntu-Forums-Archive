---
title: "Processor speed manipulation"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by TMBridge on 2006-08-13
Hey guys.

I remember reading something about this in a thread somewhere, but i've looked and searched for it to no avail.

My dilemma is I have a small case and too many items therein.  Unless I keep my air conditioner on full blast 24/7, i have an overheat crash after about 2 hours, especially after video viewing.  

I am looking for a app that will allow me to change the speed at which the processor runs.  Perhaps set it so after 1 hour of idle activity, lower processor speed to 40%-50%.  Maybe thatll reduce overheating.

Thanks for your help.

---

### Post by kinematic on 2006-08-13
here's a link for enabling cpu scaling on debian...it will probably work on ubuntu as well.
[http://www.linuxquestions.org/questions/showthread.php?t=268091](http://www.linuxquestions.org/questions/showthread.php?t=268091)
if you get it to work you right click in the empty space in the gnome panel....select "add to panel" and select the cpu applet so you can see at what frequency it's running.
with kubuntu you can use superkaramba and a widget from kde-look.org.

---

### Post by hecato on 2006-08-13
I have the applet, but CPU [only 2 frequencies?]("http://ubuntuforums.org/showthread.php?t=235057") is the problem I have... or perhaps is not a problem????


I guess I have all the things in that link you put. Tougth doing

> 
modprobe acpi cpufreq_userspace cpufreq_powersave
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.15-23-amd64-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): Unknown symbol in module, or unknown parameter (see dmesg)

in lsmod they ares listed.. I guess
> 
lsmod
Module                  Size  Used by
powernow_k8            12992  0
cpufreq_powersave       3328  0
cpufreq_stats           8264  0
cpufreq_userspace       9184  1
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
freq_table              6464  2 powernow_k8,cpufreq_stats
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
pcc_acpi               16128  0
sony_acpi               7188  0
ac                      7176  1 acpi_sbs
dev_acpi               15364  0
processor              29224  2 powernow_k8,thermal


Can you say me if I can have more than 2 frecuencies to do???, also in the help file there is a list of frequencies.. but I cant see at less the 2 frecuencies taht I have...

[IMG]http://img116.imageshack.us/img116/9543/frequencyoo6.jpg[/IMG]


There is only preferences, help, about, delete from, move, block to options are listed, and not like in the help file that display the list of the frecuencies.


Hope you can help me of clarify ( I will like at less have a 1.5Ghz... or even 750Mhz)

---

