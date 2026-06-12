---
title: "How to unload a kernel module?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-03
Hi,

the Feisty kernel has a buil-tin module called SPM that is known to make the CPU scaling not work properly when the computer is on AC. I'd like to unload that module but don't know how to do this. I know that it is possible to load non compiled modules by placing them in /etc/modules but is it possible to unload a module that is compiled in the kernel......without having to recompile a new kernel to exclude it???

Thanks

---

### Post by Cypher on 2007-05-03
No, a compiled-in Kernel module cannot be unloaded. It is part of the Kernel that is running, if you wish to exclude some functionality, then you can either not compile it at all, or compiel it as a loadable module (.ko)..

---

### Post by kilou on 2007-05-03
Thanks for the reply. Does it mean that I will need to "build" a Vanilla kernel and exclude (not compile, leave it as a loadable module) the SMP module? Can I do that with a Ubuntu kernel? I know how to compile a Vanilla kernel but have no idea how to do that with a Ubuntu one....

---

