---
title: "Kernel version 2.6.20-15 vs 2.6.20-16"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-06-09
When I turn on my computer, I get choices for kernel 2.6.20-15 and 2.6.20-16. What are the differences, and if 15 is just an older version, should I uninstall that? How would I uninstall it?

---

### Post by Bachstelze on 2007-06-09
If -16 is working fine, you should be safe uninstalling -15. Remove it in Synaptic (package is called linux-image-VERSION).

---

### Post by Bohlio on 2007-06-09
The advice I've seen, is always keep two kernels. The newest, and the previous one. I've been having problems with kernel 16, It messed up my sound somehow, gave me two "Ghost" cd rom drives, and disabled my DVD+-WR drive. Im sticking with kernel 15 for now. If you dont want to see the kernel in the Grub boot menu, but still want it around incase anything goes wrong, comment out the kernel 16 entrys in your /boot/grub/menu.lst file by adding # in front of those lines.

---

### Post by tombug on 2007-06-09
> **Bohlio said:**
> The advice I've seen, is always keep two kernels. The newest, and the previous one. I've been having problems with kernel 16, It messed up my sound somehow, gave me two "Ghost" cd rom drives, and disabled my DVD+-WR drive. Im sticking with kernel 15 for now. If you dont want to see the kernel in the Grub boot menu, but still want it around incase anything goes wrong, comment out the kernel 16 entrys in your /boot/grub/menu.lst file by adding # in front of those lines.

im having the same issues with 16, and because of that ill start with 15 for now
but there is an update for 16 and i not sure if i wanna waste the time installing it

---

### Post by SlaughterDog on 2007-06-11
Thanks. I've noticed that kernel 16 doesn't think I need ATI proprietary drivers, so things lag. So can you tell me a bit about the differences of the kernels? How often do they come out with a new kernel, and then when do you think 16 will be pretty stable? I'm using 15 for the time being.

---

