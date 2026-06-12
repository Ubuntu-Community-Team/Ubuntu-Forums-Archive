---
title: "Booting issue clarification"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-09-04
I have created a boot CD using 2.6.20.16 kernel image. 
I am presently using 2.6.22.10 kernel.
Can any one please clarify whether I can use the boot CD using one kernel image to boot into other image or I have to create another boot CD with the new kernel?
Thanks
:confused:

---

### Post by jamvegan on 2007-09-04
Just to be sure what you mean by boot CD: this is a disc which contains the first stage of grub, which would normally be installed in the MBR?  (As opposed to a Live CD which contains the boot files *and* the kernel to be booted?)  Actually, either way it is only going to contain boot menu entries that were relevant when you created the CD.

You should be able to use it to boot other kernels, but you would have to manually edit the grub commands every time that you boot.  You could do that by highlighting the entry for 2.6.20.16, typing "e" (if I am remembering correctly--the bottom of the grub screen should tell you), changing any reference to 2.6.20.16 to 2.6.22.10, and then typing "b".  If the CD is how you always boot into Ubuntu, then I think that creating a new one would be the easiest way to go.

Hope this helps! :)

---

