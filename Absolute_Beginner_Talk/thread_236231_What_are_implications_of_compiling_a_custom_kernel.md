---
title: "What are implications of compiling a custom kernel?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-08-14
Hello everyone!

I was just about to compile a kernel from [http://kernel.org](http://kernel.org)

However, before that I want to know whether Ubuntu supports user compiled kernels, or Ubuntu is custom made to work only with the kernels from the repos. 

That said and done, here are my questions. 

For my current kernel, I have installed a package that goes 'linux-kernel-headers-$(uname-r)'. What does this package provide? Will I have this package if I custom build a kernel? 

Again, I also have a package called linux-restricted-modules. What about this? Of course I won't have such a package if I compiling my own kernel. So how can I get one? 

Finally, what are the applications that are likely to break if I create a custom kernel? Something like ndiswrapper or fglrx drivers maybe?

---

### Post by harisund on 2006-08-14
wah? 2 hours and already vanished? Should I repost in some other part of the forum perhaps? Where more people read than write? Or where people have compiled their own kernels? 

Or don't Ubuntu users compile their own kernels?

---

### Post by PriceChild on 2006-08-14
Check this out:

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

I don't see the point in custom kernels, you won't see much of a speed boost, and i've always found side effects.

---

### Post by mlind on 2006-08-14
> **harisund said:**
> Hello everyone!

I was just about to compile a kernel from [http://kernel.org](http://kernel.org)

However, before that I want to know whether Ubuntu supports user compiled kernels, or Ubuntu is custom made to work only with the kernels from the repos. 

That said and done, here are my questions. 

For my current kernel, I have installed a package that goes 'linux-kernel-headers-$(uname-r)'. What does this package provide? Will I have this package if I custom build a kernel? 

Again, I also have a package called linux-restricted-modules. What about this? Of course I won't have such a package if I compiling my own kernel. So how can I get one? 

Finally, what are the applications that are likely to break if I create a custom kernel? Something like ndiswrapper or fglrx drivers maybe?

Ubuntu supports vanilla kernels without problems. Compile your kernel (and kernel headers) using make-kpkg that's provided by **kernel-package**. 

If you need kernel headers for vanilla kernel, execute kernel_headers target (or binary-arch to get both kernel and headers). You can compile restricted modules for vanialla kernel too, but it's easier to just compile ndiwrapper and gfx kernel modules using module-assistant or another method.

Most of your questions have been already answered on HOWTO section, just search for threads about custom kernel.

---

