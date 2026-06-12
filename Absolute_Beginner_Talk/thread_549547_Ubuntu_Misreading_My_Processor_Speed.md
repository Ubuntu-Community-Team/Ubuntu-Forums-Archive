---
title: "Ubuntu Misreading My Processor Speed"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by The Catalyst on 2007-09-12
I bought a PC from Wal-Mart with a ~2.4ghz AMD64 processor.

I got rid of the horrid disease known as Vista and installed Ubuntu (x86 - Feisty).

I installed Ubuntu and everything but, it reads my processor as 1.0ghz.

Then I realized my PC is AMD64, so I tried to install Ubuntu for AMD64.  Corrupt disk every time, I've tried a lot of burn speeds and stuff and re-downloaded the ISO and got a total of 10 corrupt disks (or atleast, won't install)

Is my processor really only 1.0ghz and I got owned by Wal-Mart?  Or is Ubuntu misreading it?

---

### Post by overdrank on 2007-09-12
> **The Catalyst said:**
> I bought a PC from Wal-Mart with a ~2.4ghz AMD64 processor.

I got rid of the horrid disease known as Vista and installed Ubuntu (x86 - Feisty).

I installed Ubuntu and everything but, it reads my processor as 1.0ghz.

Then I realized my PC is AMD64, so I tried to install Ubuntu for AMD64.  Corrupt disk every time, I've tried a lot of burn speeds and stuff and re-downloaded the ISO and got a total of 10 corrupt disks (or atleast, won't install)

Is my processor really only 1.0ghz and I got owned by Wal-Mart?  Or is Ubuntu misreading it?

Hi could you post the output of the command 
```
cpufreq-info -l
```
That is a lower case L.
I am  running a AMD 64 3200 and the max is 2000.

---

### Post by bsharp on 2007-09-12
Well, I don't have a AMD processor, but I remember reading that some people are having some problems with the Cool 'n Quiet feature.  You can check your actual clock speed in your POST tests while it is booting up or if there is a boot logo you should be able to go into your BIOS settings to see it there.

---

### Post by The Catalyst on 2007-09-13
cpufreq-info output:

1000000 2400000

translation please :P

i'm checking in BIOS right now and I'll edit post when I find out what it says.

---

### Post by overdrank on 2007-09-13
> **The Catalyst said:**
> cpufreq-info output:

1000000 2400000

translation please :P

i'm checking in BIOS right now and I'll edit post when I find out what it says.

```
Manual PagesApplications
cpufreq-info(1)
NAME
cpufreq-info - Utility to retrieve cpufreq kernel information
SYNTAX
cpufreq-info [options]
DESCRIPTION
A small tool which prints out cpufreq information helpful to developers and interested users.
OPTIONS
-c --cpu <CPU>
     <CPU> number which information shall be determined about.
-e --debug
    Prints out debug information.
-f --freq
    Get frequency the CPU currently runs at, according to the cpufreq core.
-w --hwfreq
    Get frequency the CPU currently runs at, by reading it from hardware (only available to root).
-l --hwlimits
    Determine the minimum and maximum CPU frequency allowed.
-d --driver
    Determines the used cpufreq kernel driver.
-p --policy
    Gets the currently used cpufreq policy.
-g --governors
    Determines available cpufreq governors.
-a --affected-cpus
    Determines which CPUs can only switch frequency at the same time.
-o --proc
    Prints out information like provided by the /proc/cpufreq interface in 2.4. and early 2.6. kernels.
-m --human
    human-readable output for the -f and -w parameters.
-h --help
    Prints out the help screen.
REMARKS
You cant specify more than one of the output specific options -o -e -a -g -p -d -l -w -f.
You also can't specify the -o option combined with the -c option.
FILES
/sys/devices/system/cpu/cpu*/cpufreq/ 
/proc/cpufreq (deprecated) 
/proc/sys/cpu/ (deprecated) 
AUTHORS
Dominik Brodowski <linux@brodo.de> - author
Mattia Dongili<malattia@gmail.com> - first autolibtoolization
SEE ALSO
cpufreq-set(1)

```
That command tell you the frequency that your cpu runs at.
ie 1000 and 2400

---

### Post by The Catalyst on 2007-09-13
Well, I've got interesting results:

I disabled Cool&Quiet (although I'm not sure I like the idea of Hot&Loud heh) and booted up Ubuntu, checked my Hardware in Cedega and clicked Auto-Update, and... now it sees it at as 2.41ghz :)

Is Cool&Quiet important?

---

