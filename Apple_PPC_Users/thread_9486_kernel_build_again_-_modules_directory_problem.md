---
title: "kernel build again - modules directory problem"
date: 2004-12-29
forum: Apple PPC Users
---

### Post by robsta on 2004-12-29
Hi, 

i'm building a customized kernel (2.6.10, ck patchset) with
$ fakeroot make-kpkg --append-to-version=ck1 --revision=1 kernel_image --initrd

But the modules are installed in 
/lib/modules/2.6.10ck1n (notice the trailng 'n')
therefore mkinitrd fails and i can't boot the kernel even if i symlink or copy the whole modules tree to 
/lib/modules/2.6.10ck1 (no trailing n)

Is there anything one can do about that?
Thanks, 
Rob

---

