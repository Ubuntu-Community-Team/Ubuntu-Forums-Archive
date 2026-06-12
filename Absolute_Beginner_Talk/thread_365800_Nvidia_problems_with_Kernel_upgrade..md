---
title: "Nvidia problems with Kernel upgrade."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by globemast on 2007-02-20
Hello,

Last week i received a kernel upgrade (2.6.17-11) through Synaptic. At that time i was running kernel 2.6.17-10 with no problem.

After reboot the X-Server failed due to an Nvidia drivers problem.

I searched through Google for proposed solutions...and came up with one solution that finally fixed my problem. But as i understand (with my limited Linux knowledge) , i must have comiled the Nvidia drivers for kernel 2.6.17-10-386.

My problem now is that every time i try to boot with another kernel 2.6.17-10-generic or 2.6.17-11-generic i get the same X-Server problem i was getting before.

Is there any way i can get the Nvidia drivers working for all kernels and for all upcoming kernel upgrades?

Thank you in advanced.

---

### Post by igknighted on 2007-02-20
> **globemast said:**
> Hello,

Last week i received a kernel upgrade (2.6.17-11) through Synaptic. At that time i was running kernel 2.6.17-10 with no problem.

After reboot the X-Server failed due to an Nvidia drivers problem.

I searched through Google for proposed solutions...and came up with one solution that finally fixed my problem. But as i understand (with my limited Linux knowledge) , i must have comiled the Nvidia drivers for kernel 2.6.17-10-386.

My problem now is that every time i try to boot with another kernel 2.6.17-10-generic or 2.6.17-11-generic i get the same X-Server problem i was getting before.

Is there any way i can get the Nvidia drivers working for all kernels and for all upcoming kernel upgrades?

Thank you in advanced.

The short answer? no.  So long as nvidia refuses to release open drivers that is.  Each kernel needs a specifically built module to interact with the driver, and there can only be one of those.  So you are stuck with the newest kernel when using the nvidia driver.  I can't speak for Ubuntu & nvidia, but it is possible that the nvidia-glx package in apt (if you installed that way) could automatically update the kernel module, but I don't know.  I know my ATI drivers in Fedora automatically update because of the way the package is put together, if the NVIDIA ones are done well then they might too, but judging by the reaction on the forums, I doubt it.

I suppose if you new a bit of code you could write a script to check the nvidia module and the kernel version at boot and rebuild the module if need be.  To leave this on every boot would slow the boot process, but it would help the issue.

---

### Post by tseliot on 2007-02-20
You can install Envy and launch it every time the kernel is updated (after the Xserver crashes):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by mikewhatever on 2007-02-20
I had a similar problem when moving from 2.6.17-10-generic to 2.6.17-11... Running envy fixed the xserver problem for the new one, but broke the old. There appears to be no simple way of making both work. Lucky for me, I don't really need the old kernel and I was wondering why do you have two different ones. One more thing, does the 2.6.17-10-386 still work?

---

### Post by coolen on 2007-02-20
I had a similar problem...I managed to get the new kernel working, but it had a dependency on the 386 kernel (I was using generic before). Now, some applications aren't installing because they're unsupported for my kernel.
I didn't use Envy to get them (I just prefer to know what's happening :)), but can I change my apt entry to get one that works with the generic kernel? I have no need to use the 386 kernel over generic, other than that my current driver only works with it.
Apt entry is:
```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```

---

### Post by hartz on 2007-02-20
Sigh, if only Linus would make the kernel-driver interface stable.

---

### Post by globemast on 2007-02-21
Ok,

Do you have any link on how to install and build the nvidia drivers for 2.6.17-11-generic kernel?

Also i seem to have a problem with X11 configuration.... the resolution settings are not saved and everry time i reboot i need to reset my configuration with Nvidia X Server Settings

Thanks in advance.

---

### Post by globemast on 2007-03-06
i seem to have a problem with X11 configuration.... the resolution settings are not saved and everry time i reboot i need to reset my configuration with Nvidia X Server Settings

Any suggestions?

Thanks in advance.

---

### Post by edwardLS on 2007-03-06
Is the resolution that you are setting in nVidia X Server Settings in the file: /etc/X11/xorg.conf?

---

