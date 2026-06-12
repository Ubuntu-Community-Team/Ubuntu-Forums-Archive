---
title: "How to remove old Kernal"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-04
Well I shure you all know about the new kernal well if you are not haveing any problems with the new kernal how would you remove the old kernal.

---

### Post by daimaru on 2007-06-04
if you dont want it to show up anymore on your boot screen, 
edit your /boot/grub/menu.lst file and remove the .15 entries .

---

### Post by Inxsible on 2007-06-04
Removing the grub menu entries will not remove the kernel. If you really want to remove the kernel you should search for it in synaptic and uninstall them there.

However, you should be careful in doing this, as if you remove the old kernels you wont be able to boot into the machine if the newer ones give you problems. Test the new kernel thoroughly before uninstalling the older one.

Rule of Thumb : Keep at least one older and stable kernel around just in case :)

---

### Post by NeoGreen on 2007-06-04
Just what Inxsible said, it is wise to keep an old kernel handy, cause you never know when you run into a kernel panic.

---

### Post by gunbladeiv on 2007-06-04
can i install kernel by using source tarball?

how?

---

### Post by jonward0690 on 2007-06-04
> **Inxsible said:**
> Removing the grub menu entries will not remove the kernel. If you really want to remove the kernel you should search for it in synaptic and uninstall them there.

However, you should be careful in doing this, as if you remove the old kernels you wont be able to boot into the machine if the newer ones give you problems. Test the new kernel thoroughly before uninstalling the older one.

Rule of Thumb : Keep at least one older and stable kernel around just in case :)

Ok well looked in the synaptic package manager and could not find the Kernal to remove

---

### Post by Inxsible on 2007-06-05
What kernel are you trying to remove ?

if 2.6.20-15 search for "kernel 2.6.2.-15"  -- without quotes of course.

you will find 3 packages installed linux-images-generic or something to that effect. i dont rbr the exact names. uninstall all 3 to remove the kernel

---

### Post by jonward0690 on 2007-06-05
> **Inxsible said:**
> What kernel are you trying to remove ?

if 2.6.20-15 search for "kernel 2.6.2.-15"  -- without quotes of course.

you will find 3 packages installed linux-images-generic or something to that effect. i dont rbr the exact names. uninstall all 3 to remove the kernel

Well thanks for the info all remember,but your right I think I am going to keep the old kernal as a fail safe.

---

### Post by bromix on 2007-06-05
Use Synaptic... search for   linux-image      Uncheck the box next to the old kernel.   But...like everyone said, I always keep the current AND the last stable kernel available to boot to.

---

### Post by shae on 2007-06-05
If you want to install a kernel from source, you have to compile the kernel.  It is a rather simple process.  For instructions check [The Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=vanilla").  I can confirm those instructions work with 2.6.21 vanilla with ck2 patches.

---

