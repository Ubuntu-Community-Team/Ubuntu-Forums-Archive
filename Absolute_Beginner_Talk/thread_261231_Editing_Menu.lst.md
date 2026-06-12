---
title: "Editing Menu.lst ????"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-09-20
I upgraded to the k-7 kernel & I installed the update now I have a grub menu that looks like this

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

I'm sure I don't need them all but which ones can I SAFELY remove? I started to delete the boot selections with kernel 2.6.15-26 but I believe that it is wiser to ask first.

---

### Post by jISh on 2006-09-20
You could safetly remove all but the first four (which you should keep, two for regular boot and two recovery modes). 

The rest are for restoring your old kernel if one breaks.

Edit: And leave the memtest one at the bottom alone.

---

### Post by aysiu on 2006-09-20
The best way to remove old kernels is through a package manager (using Synaptic, Adept, or *aptitude*). Search for the phrase *linux-image*

---

