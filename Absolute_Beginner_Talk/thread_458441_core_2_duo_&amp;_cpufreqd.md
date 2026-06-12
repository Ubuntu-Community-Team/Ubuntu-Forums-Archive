---
title: "core 2 duo &amp; cpufreqd"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-05-29
hi.
i'm trying to setup a processor-freq-scalling on my laptop.
i wanna to use a conservative gowernor all time when i'm on ac-adapter and a powersave gowernor when i'm on batteries.

this is my /etc/cpufreqd.conf file

# this is a comment
# see CPUFREQD.CONF(5) manpage for a complete reference
#
# Note: ondemand/conservative Profiles are disabled because
# they are not available on many platforms.

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=4
#enable_remote=1
#remote_group=root
[/General]

#[acpi]
#acpid_socket=/var/run/acpid.socket
#[/acpi]

[Profile]
name=powersave
minfreq=1000000
maxfreq=1000000
policy=powersave
[/Profile]

[Profile]
name=conservative
minfreq=1000000
maxfreq=2000000
policy=conservative
[/Profile]


##
# when AC use performance mode

[Rule]
name=conservative
ac=on # (on/off)
profile=conservative
[/Rule]

[Rule]
name=powersave
ac=off
profile=powersave
[/Rule]

i've added a cpufreq_powersave and cpufreq_conservative and acpi_cpufreq into my /etc/modules file, they are loaded automatically on start.

i can switch into conservative mode only by

sudo cpufreq-set -c 0 -g conservative

by defoult it uses performance gowernor

its my cpufreq-info results (after cpufreq-set -c 0 -g conservative)
szymon@linugrat:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
driver: acpi-cpufreq
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 1000 MHz - 2.00 GHz
available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
available cpufreq governors: powersave, conservative, performance
current policy: frequency should be within 1000 MHz and 2.00 GHz.
The governor "conservative" may decide which speed to use
within this range.
current CPU frequency is 1000 MHz.
analyzing CPU 1:
driver: acpi-cpufreq
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 1000 MHz - 2.00 GHz
available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
available cpufreq governors: powersave, conservative, performance
current policy: frequency should be within 1000 MHz and 2.00 GHz.
The governor "conservative" may decide which speed to use
within this range.
current CPU frequency is 1000 MHz.

when i switch into tty1 (ctr + alt +f1) i see only something like that :

* CPUFreq-utilities: setting conservative CPUFreq governor..... [fail]

any ideas whats wrong?

szymon


i use FF ubuntu, default kernel
2.6.20-15-generic

---

