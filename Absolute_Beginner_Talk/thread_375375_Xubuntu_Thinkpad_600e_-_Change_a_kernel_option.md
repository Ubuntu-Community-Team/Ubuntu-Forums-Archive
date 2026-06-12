---
title: "Xubuntu Thinkpad 600e - Change a kernel option"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by harryc on 2007-03-03
I want to change just one kernel option in the Xubuntu install on my 600e. Specifically it is to set -  Power Management Options > APM Bios Support > "Use real mode APM Bios call to power off" to Yes. I have never recompiled a kernel or changed a kernel option on a kernel in Ubuntu or Xubuntu. Can anyone point me to a tutorial or lay out a few basic steps?

---

### Post by kerry_s on 2007-03-03
There's several ways you can do it and not have to recompile the kernel.

You can just uninstall it->
press alt+F2 type gksu synaptic, click find type " apmd " right clik and mark for complete removal

or

gksu mousepad /boot/grub/menu.lst
put " noapmd apmd=off " at the end of the boot line.

kernel		/boot/vmlinuz-2.6.20-8-386 root=UUID=e10b57e0-ad39-46c8-a2e2-6ff61cd76c55 ro  quiet silent noapmd apmd=off

(it might be apm instead of apmd, try with and with out the "d")

or 
add apm  to bad_list/blocklist in /etc/modprobe.d

There's more but i can't think of them all, just try google.

---

### Post by harryc on 2007-03-03
> **kerry_s said:**
> 
You can just uninstall it->
press alt+F2 type gksu synaptic, click find type " apmd " right clik and mark for complete removal
Thanks for the reply, but I don't think that setting "Use real mode APM Bios call to power off" actually disables APM. It's just a kernel option 'for APM'. I believe I need APM for some type of power management. ACPI is already disabled because of another problem.

---

### Post by kerry_s on 2007-03-03
So you have both disabled?
Can you stop beating around the bush and say exactly what is wrong, that you feel you need to be messing with power management in the first place?
Do you know which your system supports apm, acpi, both?


The installer says that apm is already off by default unless you pass the option "apm=on"

```
Utilities for Advanced Power Management (APM) 
On laptop computers, the Advanced Power Management (APM) support
provides access to battery status information and may help you to
conserve battery power, depending on your laptop and the APM
implementation.  The apmd program also lets you run arbitrary programs
when APM events happen (for example, you can eject PCMCIA devices when
you suspend, or change hard drive timeouts when you connect the battery).

This package contains apmd(8), a daemon for logging and acting on APM
events; and apm(1), a client that prints the information in /proc/apm
in a readable format.

apmd is notified of APM events by the APM driver in the kernel.

Debian kernels are built with APM support but it is disabled by
default.  You need to boot the kernel with the "apm=on" option if you
want to enable the driver. (You may need to add this option to your
lilo command line.)

In most cases, users may want to know that there are newer power
management schemes, like ACPI.

 Homepage: http://www.worldvisions.ca/~apenwarr/apmd/
```

---

### Post by harryc on 2007-03-03
It supports APM and ACPI, but in order for the PCMCIA wireless card to work, ACPI must be disabled. I have apm=on and acpi=off on the kernel line in menu.lst. I am trying to fix the inability to power off the **laptop**. The aforementioned kernel option is known to fix this issue. 

[http://www.linuxquestions.org/questions/t373814.html](http://www.linuxquestions.org/questions/t373814.html)

> This is a kernel problem. The older Thinkpads have a problem with their BIOS. To solve it you have to recompile the kernel and set the option in
Power Management Options > APM Bios Support > "Use real mode APM Bios call to power off" to YES. After recompiling the kernel it should work.

---

### Post by kerry_s on 2007-03-03
Take a look at this thread-> [http://ubuntuforums.org/showthread.php?t=715](http://ubuntuforums.org/showthread.php?t=715)

---

### Post by harryc on 2007-03-04
kerry_s, thanks for pointing me to that thread, but I had no luck there. That thread recommends (3) things. First is to sudo modprobe apm and then try to power down. apm is already loaded per lsmod and acpi is not. The second thing it recommends is to update your machines BIOS. I have the latest BIOS installed. Finally it recommends to add acpi=force to the kernel line in Grub. As I stated previously, this is not an option for me because I have a wifi card (Orinico Gold - PCMCIA) that jumps ship everytime it smells acpi. So, we're back to my original request. How do I simply change one kernel option and recompile a kernel in Ubuntu. Surely someone has done this?

---

### Post by harryc on 2007-03-04
OK, I found this howto for Dapper, but my Xubuntu is Edgy. Do I need to make any changes to the howto for Edgy?

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

---

### Post by kerry_s on 2007-03-04
That looks right there standard compiling instructions. Make sure you back up anything important. Compiling a kernel is not the easiest thing and it might take you a couple of tries to get it right. Make sure you jot down any commands you might need to use to perform a system rescue, have a live cd handy, if all else fails wipe it and try again. Good luck.

---

### Post by harryc on 2007-03-04
Following up to complete this thread, the kernel "Use real mode APM Bios call to power off" option did nothing to fix the problem (on a positive note I did learn how to compile a .deb kernel), but this did fix it;

> POWER
The 600E has a few problems with how it does power. Since we kinda disabled ACPI before (implementation on the 600E is there, but buggy) we have to do the following to make sure Shutdown works. In a console window:

nano -w /etc/modprobe.d/power

add the following bit of code to the new file:

options apm power_off=1 realmode_power_off=1

And then EXIT from the file and reboot.
Reference - [http://www.blog.savant.be/linux/ubuntu-610-edgy-on-a-thinkpad-600e-2645-57u/15/](http://www.blog.savant.be/linux/ubuntu-610-edgy-on-a-thinkpad-600e-2645-57u/15/)

Thanks again kerry_s for the assist.

---

