---
title: "two new lines in grub menu"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by housam on 2006-12-23
After updating Dapper and installing the linux-686-smp, I've got two lines more in my grub menu. each one of them booting Dapper.
the original is 2-6-15-23-386
the others are 2-6-15-27-386 & 2-6-15-27-686.
Are these a different version of dapper ?
Why updating gives another bootable kernel and not just updating the original?

---

### Post by insane_alien on 2006-12-23
The 2-6-15-27-686 kernel is the one you installed and should be at the top. this is the optimised on you should probably use if it works for you.

the reason the kernels are left behind is incase the new kernel doesn't work.
some people like compiling the very latest version of a kernel (for testing, development or for the sheer hell of it) but also want a stable system. for other people its just that the latest kernels might not work on their hardware. if it doesn't they can always boot into the older kernel to have a working system. if the kernel works for you then there is no harm in deleting the old kernel.

---

### Post by housam on 2006-12-23
Thanks for the reply.

---

