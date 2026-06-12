---
title: "TI PCIxx21"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jadda on 2007-04-19
Hi
Can't make my sd card mount.

arne@arne-laptop:~$  sudo modprobe tifm_sd
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/drivers/misc/tifm_core.ko': No such file or directory
FATAL: Error inserting tifm_sd (/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/tifm_sd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
arne@arne-laptop:~$ dmesg
[  314.120000] tifm_sd: Unknown symbol tifm_eject
[  314.120000] tifm_sd: Unknown symbol tifm_register_driver
[  314.120000] tifm_sd: Unknown symbol tifm_unmap_sg
[  314.120000] tifm_sd: Unknown symbol tifm_map_sg
[  314.120000] tifm_sd: Unknown symbol tifm_unregister_driver
[  377.100000] tifm_sd: Unknown symbol tifm_eject
[  377.100000] tifm_sd: Unknown symbol tifm_register_driver
[  377.104000] tifm_sd: Unknown symbol tifm_unmap_sg
[  377.104000] tifm_sd: Unknown symbol tifm_map_sg
[  377.104000] tifm_sd: Unknown symbol tifm_unregister_driver
[  530.608000] tifm_sd: Unknown symbol tifm_eject
[  530.608000] tifm_sd: Unknown symbol tifm_register_driver
[  530.608000] tifm_sd: Unknown symbol tifm_unmap_sg
[  530.608000] tifm_sd: Unknown symbol tifm_map_sg
[  530.608000] tifm_sd: Unknown symbol tifm_unregister_driver
[  624.392000] tifm_sd: Unknown symbol tifm_eject
[  624.392000] tifm_sd: Unknown symbol tifm_register_driver
[  624.392000] tifm_sd: Unknown symbol tifm_unmap_sg
[  624.396000] tifm_sd: Unknown symbol tifm_map_sg
[  624.396000] tifm_sd: Unknown symbol tifm_unregister_driver
[  664.816000] tifm_sd: Unknown symbol tifm_eject
[  664.816000] tifm_sd: Unknown symbol tifm_register_driver
[  664.820000] tifm_sd: Unknown symbol tifm_unmap_sg
[  664.820000] tifm_sd: Unknown symbol tifm_map_sg
[  664.820000] tifm_sd: Unknown symbol tifm_unregister_driver

Any ideas?
got the problem when I updated to Feisty.  Appreciate any help=)

---

### Post by jadda on 2007-04-20
Is this a kernel specific fault? are antbody else experiencing the same problems?

---

### Post by Bachstelze on 2007-04-20
Seems the Ubuntu devs forgot to include this module in their kernel build. You could build yourrself a whole kernel from vanilla sources.

---

### Post by jadda on 2007-04-20
Vanilla sources? hmmm....could you try to explain this? I am quite the noob...

---

### Post by Bachstelze on 2007-04-20
"Vanilla sources" mean kernel sources taken straight from [http://www.kernel.org](http://www.kernel.org)

There are a few HOWTO's on this forum about building custom kernels.

---

### Post by jadda on 2007-04-20
Ok.
I look into it. Thanks=)

---

### Post by jadda on 2007-04-20
um...one more question...would it be possible to replace the kernel with the kernel used in edgy?

---

### Post by Bachstelze on 2007-04-20
Hmmn in fact the module is in Feisty but with the 2.6.20-14 kernel, I guess you could just install it.

---

### Post by jadda on 2007-04-20
I am sorry, trying to learn, and suspect I think a lot harder than it has to be when you say "just install it". how?

---

### Post by Bachstelze on 2007-04-20
Search for it in Synaptic, it should be called linux-image-2.6.20-14-generic.

---

