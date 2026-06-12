---
title: "(Very) lightweight distros with kexec capable kernels?"
date: 2012-12-15
forum: Any Other OS
---

### Post by jwbrase on 2012-12-15
I have an old Pentium machine with 40 MiB of RAM that I've been running a hard drive install of DSL on. DSL is multibooted via Grub with DOS (for nostalgic gaming) and whatever other OS I might happen to be experimenting with at the time.

The problem is that I reboot the machine to switch OS's fairly often, and the BIOS POSTs painfully slowly, so I'd like to be able to kexec from Linux straight into GRUB. DSL only has a 2.4 kernel, however, and kexec was introduced in 2.6.13.

So does anybody know of a distro that will fit into 40 MB of RAM that has a >=2.6.13 kernel, or an older kernel with kexec backported in, or of any way of getting a kexec-capable kernel into DSL (though module compatibility issues will probably make that a no-go.), or of any other way of bypassing POST?

---

### Post by SpaceAviator on 2012-12-15
You know what you can do? Compile your own kernel :D Its fun an easy!

---

### Post by jwbrase on 2012-12-16
> **SpaceAviator said:**
> You know what you can do? Compile your own kernel :D Its fun an easy!

For that to be of any use I'd have to find a patch backporting kexec to kernel 2.4.31, which I haven't had much luck with yet.

---

