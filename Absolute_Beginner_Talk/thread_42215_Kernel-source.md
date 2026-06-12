---
title: "Kernel-source?"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by cvogel on 2005-06-16
Hello.  I'm fairly new to linux and am trying to install the latest madwifi module.  Apparently, the one that comes with ubuntu is too old.  I need to specify my KERNELPATH but unfortunately, /usr/src has no kernel directory in it... just the headers that I've installed.  

My kernel is: 2.6.10-5-amd64-generic

"export KERNELPATH=/usr/src/linux-2.6.10-5-amd64-generic" doesn't work because that directory does not exist.

What do I need to do get the kernel there so that I can set the correct path and compile my module?

Thanks

---

### Post by desdinova on 2005-06-16
Search synaptic for "linux-source"

---

### Post by cvogel on 2005-06-16
Thanks, I appreciate it.  That package will install the correct source? The amd64 one?

---

### Post by desdinova on 2005-06-16
[QUOTE=cvogel]Thanks, I appreciate it.  That package will install the correct source? The amd64 one?[/QUOTE]

The source code is whats called platform independent = the same for all

---

### Post by az on 2005-06-16
Use linux-tree

It is easier and includes all the ubuntu patches and configs...

---

### Post by cvogel on 2005-06-16
Great! :) Thanks all.

---

### Post by desdinova on 2005-06-16
Thanks very much Azz, I'll file that away for future reference ;-)

---

### Post by cvogel on 2005-06-16
so once I've downloaded the linux-tree package, what do I do with it?

Thanks

---

