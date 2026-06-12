---
title: "Cannot load a kernel module, why?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-03
Hi,

I have a MSI S260 laptop and would like to get more stuff supported. I noticed there is a module called msi-laptop that should be loaded. I'm trying to load it with **sudo modprobe msi-laptop** but get the following:

FATAL: Error inserting msi_laptop (/lib/modules/2.6.20-15-generic/kernel/drivers/misc/msi-laptop.ko): No such device

Why is this not working or how should I do to have it work?

Thanks

---

### Post by Cypher on 2007-05-03
Check on '/var/log/messages' and 'dmesg' and see if there is any more info as to why the module wouldn't load. The fact that it's saying "no such device" might mean that the module supports some specific hardware that isn't available on your laptop..

---

### Post by Bachstelze on 2007-05-03
"No such device" means there is no hardware supported by this module on your system (you get it for example when you try to modprobe a driver for AMD processors while your machine has an Intel). Maybe your laptop is too new and the module doesn't support it yet.

---

### Post by kilou on 2007-05-03
I can't find anything related to msi-laptop in both dmesg and /var/log/messages (also I tried running sudo modprobe msi-laptop again and it didn't print anything in /var/log/messages).

It is possible that my particular laptop is not supported by msi-laptop but I read somewhere that it is possible to force the use of this module by using the option force=1 but I don't know how this is supposed to be achieved.

Should I try sudo modprobe msi-laptop force=1 or add msi-laptop force=1 to the list in /etc/modules ???

EDIT: sudo modprobe msi-laptop force=1 doesn't produce any error message....so I guess this works.

---

### Post by josephus on 2007-05-03
why do you think that this module should be loaded in the first place, other than the fact that you have a msi laptop?

---

### Post by Bachstelze on 2007-05-03
I don't think you should force the load of the module, bad things might happen...

---

### Post by Cypher on 2007-05-03
> **HymnToLife said:**
> I don't think you should force the load of the module, bad things might happen...
Technically, since the initial loading of the module resulted in "no such device", forcing it means that it's loaded but isn't actually attached to any device or providing any service. So it's just loaded and taking up memory space but providing no functionality..

---

### Post by kilou on 2007-05-03
Well not really because I need that module to control the LCD brightness automatically. From what I could read this module is designed for the MSI S270 laptop only but it can work with others however others must use the force=1 option to load it. Now that this module is loaded I can control the LCD brightness with:

echo "n" > /sys/devices/platform/msi-laptop-pf/lcd_level   with n:0-8

This is useful because now I can write a script in etc/acpi/ac.d and etc/acpi/battery.d that launch this command and adapt the LCD brightness when I switch on/off battery :) 


Why is it dangerous to force load of a module? What can this do at worst?

---

### Post by Cypher on 2007-05-03
It is strange that the module is working and had to be forced into action as opposed to just loading normally. 

The danger of forcing a module (a feature that can be enbaled/disabled in the Kernel) depends on the kind of module and how well it is written. If you were to try to load a module not meant for your computer, it should gracefully fail. If you force the load against it's better judgement, a well written module would just sit idlely as it has no real work to do. However, an ill written module could just as easily try to function as if it were operating on the right device and take up either unnecessary CPU or Memory resources in the process..

---

### Post by kilou on 2007-05-03
As far as I know the guy who wrote that module made it exclusively for the S270 laptop and apparently there is something that prevent its use on other laptop probably. However the module can work on different MSI laptop such as mine. At least for now I don't see any problem and the feature works perfectly :)

---

