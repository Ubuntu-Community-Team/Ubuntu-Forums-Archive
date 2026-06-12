---
title: "Mac Mini Sleep Help"
date: 2006-09-21
forum: Apple PPC Users
---

### Post by snoe on 2006-09-21
Hi there, I've recently installed dapper on my G4 PPC Mac Mini and things are working great except I can't get it to sleep. 

When I have gone through the gnome powermanagement screen and selected the sleep on suspend option, the only thing that happens when I go logout-->suspend is my screen locks. (sorry if the terminology is not quite right, I'm not at my computer). Nothing happens when I try to sleep using the power button.

Now, I've been looking on these forums, the wikis and everything and I can't find a definitive answer. I could really use some guidance. Some clues point to lack of kernel support, but most posts I find seem to be laptop specific and don't work for me.

Some things I've found:
ACPI:
I do not have acpi-support available (not available for ppc?) so /proc/acpi doesn't exist and
```
snoe@matrix:~$ sudo acpitool
 AcpiTool v0.4.0, released 27-Nov-2005
Seems like this system lacks ACPI support or else /proc/acpi is not the place to look for ?

```

APM (--suspend does nothing, no log entries, nothing):
```
snoe@matrix:~$ sudo apm -d
APM BIOS 1.1 (kernel driver 0.5)
32-bit APM interface not supported
snoe@matrix:~$ sudo apm --suspend
snoe@matrix:~$ sudo apm --standby
apm: Invalid argument
snoe@matrix:~$ more /proc/apm
0.5 1.1 0x00 0x01 0xff 0xff -1% -1 min
snoe@matrix:~$ sudo apm -M
Line   : on
Battery: -1% (?)

```

ppbuttonsd:
```
snoe@matrix:~$ pbbuttonsd
WARNING: No event devices available. Please check your configuration.
```

dmseg:
```
snoe@matrix:~$ dmesg | grep apm
[   57.605108] apm_emu: APM Emulation 0.5 initialized.
```

The reason I need this to work on the mini is because I want to put it in my car and I'll need to have it sleep so my batteries don't drain.

---

### Post by stmiller on 2006-09-21
ACPI is n/a for ppc. Same for apm. Those don't work with the ppc hardware. Pbbuttonsd controls sleep and hibernate. And for PPC Linux, you must have an ATI graphics card for sleep to work. Nvidia and anything else will not work.

[http://pbbuttons.sourceforge.net/projects/pbbuttonsd/doc.html](http://pbbuttons.sourceforge.net/projects/pbbuttonsd/doc.html)

Try these, of if they don't work, post the output here

$ sudo pbbcmd hibernate

or 

$ sudo pbbcmd sleep

or

$ sudo pbbuttonsd sleep

or

$ sudo pbbuttonsd hibernate

---

