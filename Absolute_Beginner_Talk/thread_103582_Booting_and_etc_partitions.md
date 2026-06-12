---
title: "Booting and /etc partitions"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by muganor on 2005-12-14
Hello,

I'd like to know if it's possible to create two partitions /etc and mouting one or another at bootup to switch configurations.  It would be particuliary usefull to switch xorg.conf (ati for resume/switch display vs fglrx for 3d).  Or if you know a better way to achieve this, I'm opened to suggestions.

In my early linux days (Slackware 3.4 with lilo), I remember we could do that but I don't recall how.

Thank you

---

### Post by gruepig on 2005-12-14
Would be an interesting thing ... you'd have to have a bootloader that would allow you to pass this parameter.  I don't know of one for grub or lilo.   I don't think you could do this any later in the boot process, as you need /etc/inittab at least.

If you want to have multiple configurations for X and other services, I guess you could create separate config files and have an init script which prompts you to select one.

---

### Post by psusi on 2005-12-14
I'd add an entry to the boot menu to pass a new kernel parameter and add a script to /etc/init.d/rcS to check for that parameter and create an xorg.conf symbolic link to one or the other actual xorg.conf files that use the different settings.

---

