---
title: "Rocks Cluster Distrobution 6.1 does not boot"
date: 2014-05-08
forum: Any Other OS
---

### Post by imm0rta1 on 2014-05-08
I'm trying to run Rocks Cluster distro (ISOBooting), but i can't seem to get it to work. In grub.cfg i have:

```
         menuentry "Rocks Cluster 6.1.1" {
         set isofile="/iso/rocks-v6.1-emerald-boa.iso"
         loopback loop (hd0,5)$isofile
         linux (loop)/isolinux/vmlinuz boot=isolinux iso-scan/filename=$isofile noprompt noeject ks=cdrom:/(loop)/ks.cfg 
         initrd (loop)/isolinux/initrd.img
 }

```

I choose from the menu, it boots up, but doesn't make any further. It just sits there with blue screen. Am i missing some parameters? The original DVD boots up with a splash screen asking for a command like "build". I'm unsure how to resolve it.
Please help! Thanks! :)

---

