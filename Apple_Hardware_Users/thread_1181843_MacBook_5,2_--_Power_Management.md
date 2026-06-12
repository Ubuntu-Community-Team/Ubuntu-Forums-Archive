---
title: "MacBook 5,2 -- Power Management ?"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by UbuCocu on 2009-06-08
Hallo all,

I managed to install Ubuntu 8.10 (intrepid ibex) on my white MacBook v. 5.2. That involved setting the boot parameter

acpi=off

in the /boot/grub/menu.lst file

My question would be, with ACPI disabled (for what I know), what options do I have for power management, if any?

Would any of these work

laptop-mode-tools 

battery-stats

uswsusp

?

Any suggestions?

On the bright side, I managed to change the screen brightness and contrast to my liking using the non-open-source NVIDIA control panel which is available through the update manager.

Thanks!

---

### Post by cyberdork33 on 2009-06-08
please see this bug report:
[https://bugs.edge.launchpad.net/mactel-support/+bug/341230](https://bugs.edge.launchpad.net/mactel-support/+bug/341230)

you can also disable one of the cores and acpi will work.

---

### Post by UbuCocu on 2009-06-08
Thanks! How do I disable one core? Do I also have to set a GRUB parameter? And remove "acpi=off". I am a lot more interested in having Power Management than dual core.

---

### Post by UbuCocu on 2009-06-08
"For a more preferential temporary workaround: use nosmp or maxcpus=1 to have ACPI but only one core enabled."

From the link

[https://bugs.edge.launchpad.net/mact...rt/+bug/341230](https://bugs.edge.launchpad.net/mact...rt/+bug/341230)

I assume I have to replace

acpi=off 

with

nosmp --or-- maxcpus=1

in the 

/boot/grub/menu.lst file. Can anybody confirm this? Thanks!

---

### Post by cyberdork33 on 2009-06-08
> **UbuCocu said:**
>  I assume I have to replace

acpi=off 

with

nosmp --or-- maxcpus=1

in the 

/boot/grub/menu.lst file. Can anybody confirm this? Thanks!
yep, you could have both, but it isn't needed.

---

### Post by UbuCocu on 2009-06-09
The maxcpus=1 did the trick. I was able to reboot and see the power management tools such as the battery.

However, after installing xubuntu-desktop, it froze at GRUB load... Even re-installing Ubuntu didn't help. Is maxcpus=1 very dangerous? It seemed like an elegant solution...

---

### Post by cyberdork33 on 2009-06-10
> **UbuCocu said:**
> Is maxcpus=1 very dangerous? It seemed like an elegant solution...

I don't think it is dangerous, it just limits your system to one core.

---

