---
title: "Need Help Installing New Kernel"
date: 2007-07-24
forum: Apple PPC Users
---

### Post by jaskah on 2007-07-24
hello
i want to install an earlier kernel from feisty in order to get the sound working on my g4 titanium power book.
in this thread 
[http://ubuntuforums.org/showpost.php?p=2990910&postcount=42](http://ubuntuforums.org/showpost.php?p=2990910&postcount=42)
there is information about which kernel to use but it´s not clear to me how to install the new kernel.
any help greatly appreciated!

---

### Post by stmiller on 2007-07-24
Install this package: (save, then double click it)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-powerpc_2.6.17.1-12.39_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-12-powerpc_2.6.17.1-12.39_powerpc.deb)

That will install an older Edgy kernel.

---

### Post by jaskah on 2007-07-24
hi
thanks for your reply. it´s still not clear to me how i can boot into the newly installed kernel.
i ´ve run the deb installer and i can now see the new kernel in the boot directory
boot/vmlinux-2.6.17-12-powerpc
but when i re-start i still boot into the old kernel
vmlinux-2.6.20-16-powerpc
how can i boot into the kernel i just installed? i´ve looked in the yaboot.config file but it´s not clear to me what i have to change here.

---

