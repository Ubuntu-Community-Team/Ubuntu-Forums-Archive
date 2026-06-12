---
title: "Multiple Kernels"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by luap on 2005-12-13
I have mutilple kernels.. when i boot up and GRUB shows 2 different kernels.. one is an earlier version that i dont want anymore.. how do i go about deleting it.. i looked in synaptic and couldnt find anything

---

### Post by arpunk on 2005-12-13
Search for *kernel-image* in synaptic again... its there.

---

### Post by luap on 2005-12-13
[QUOTE=arpunk]Search for *kernel-image* in synaptic again... its there.[/QUOTE]
It's not there.. I have all the repositories too..

editted.. I think you ment linux-image.. cuz i just found it

---

### Post by arpunk on 2005-12-13
Ok, can you paste the contents of */boot/grub/menu.lst*? you can do:
```
cat /boot/grub/menu.lst | grep kernel
```
for specific output of the kernels you got installed.

---

### Post by linbetwin on 2005-12-13
It's called "linux-image" and you shouldn't uninstall your old kernel, Wait a few weeks/months and you can comment out the old kernel in the GRUB menu.lst. That is, if you don't have problems with the new kernel.

---

### Post by arpunk on 2005-12-13
[QUOTE=linbetwin]It's called "linux-image" and you shouldn't uninstall your old kernel, Wait a few weeks/months and you can comment out the old kernel in the GRUB menu.lst. That is, if you don't have problems with the new kernel.[/QUOTE]
Ohh, my mystake, forgot the name :S

---

### Post by saldie on 2005-12-13
Hey guys, when you delete the kernels through synaptic, what's the difference between "removal" and "complete removal"?

---

### Post by MagicNo14 on 2005-12-19
I'm a complete ubuntu newbie, but the synaptic tool seems to mention that complete removal means that you remove the configuration files too. I don't know if this is the only difference though.

---

