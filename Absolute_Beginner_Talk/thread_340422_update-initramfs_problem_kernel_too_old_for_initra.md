---
title: "update-initramfs problem: kernel too old for initramfs"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by franestepona on 2007-01-17
Hi, I'm having this issue:
```
fran@fransmachine:~$ sudo update-initramfs -u
Password:
update-initramfs: Generating /boot/initrd.img-2.4.27-2-686
W: kernel 2.4.27-2-686 too old for initramfs on i386
W: not generating requested initramfs for kernel 2.4.27-2-686

```

But that kernel is already uninstalled and I can't find it anywhere. It stops there and doesnt upgrade initramfs for any kernel,. Anyone knows how to solve this??

---

### Post by Rippey on 2007-01-17
try ```
sudo update-initramfs -u -k "kernelversion of the kernel you are running"
```
not realy a solution, but it'll work till you find a way to get rid of the old kernel.

---

