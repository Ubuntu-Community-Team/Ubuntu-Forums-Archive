---
title: "what is boot_cpu_data"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by strikenowhere on 2008-03-13
Hello,
I am doing some work with a third party module and when I modprobe the module I am getting an error stating:

disagrees about version of symbol boot_cpu_data
unknown symbol boot_cpu_data

Can somebody just explain what the symbol boot_cpu_data is to begin with?

Thanks,
Greg

---

### Post by kidders on 2008-03-15
Hi there,

"boot_cpu_data" is a kernel symbol. You might be interested in [http://www.promethos.org/lxr/http/ident?v=2.6.15;i=boot_cpu_data](http://www.promethos.org/lxr/http/ident?v=2.6.15;i=boot_cpu_data).

The kernel module you're using is incompatible with your kernel. To be assured of compatibility, you need to recompile it from source against your own kernel, and do so again, whenever you install a new kernel in the future.

---

