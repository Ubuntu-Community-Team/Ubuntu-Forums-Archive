---
title: "[SOLVED] Where is the kernel?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-03-23
I am hoping that I can use the kernel that Ubuntu uses. I am trying to install Gentoo but to use the same Kernel as Ubuntu. Is that possible? Does anyone know how?

---

### Post by spupy on 2008-03-23
I'm not sure you can use the Ubuntu kernel. But if you don't want to compile your own kernel right now (i guess this is the reason), why not use the kernel of the Gentoo CD? When you have the running installation with that kernel, you can try with the Ubuntu kernel.

---

### Post by igknighted on 2008-03-23
point grub to Ubuntu's /boot and use the vmlinuz link.  You will also need to copy the /lib/modules/<desired kernel> folder (and its contents) to the desired folder in gentoo.  This can cause some issues (I would manually install all 3rd party drivers like nvidia for _both_ systems in order to avoid version mismatches), but I have done it before and it works well.

---

### Post by slughappy1 on 2008-03-23
Umm, how would I do that?

---

### Post by igknighted on 2008-03-23
when you finish installing gentoo, change the path to the kernel (in the grub menu.lst) from whatever path gentoo wants to use to the one for ubuntu, **but leave the root=/dev/gentoopartition section in tact**.  You will also need to point to the system.map for the initrd, also from ubuntu's /boot IIRC.

As for moving the /lib/modules stuff, that's a simple copy and paste from one partition to the other.

If you post your gentoo menu.lst, as well as the results of the command 'ls -a /boot' (run in ubuntu) we could give you more specific advice.

Oh... since gentoo is source based, you would probably need to install the kernel-source package in ubuntu and then copy the contents of /usr/src/linux into the corresponding folder in gentoo so it could build against the kernel as well.

---

