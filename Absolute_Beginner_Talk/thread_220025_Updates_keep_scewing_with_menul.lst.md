---
title: "Updates keep scewing with menul.lst"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-20
> title		Ubuntu, kernel 2.6.15-26-k7
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-k7
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-k7 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-25-k7
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

It keep adding the 386.... The new and old 386.... Then It also adds the old K7... On top of that, the new K7 changes the path to (hd3,1) it should be (hd0,1)....bleh

edit: On top of that, the updates wants 2 update the old 386...

---

### Post by simonn on 2006-07-20
You could always read the comments in the file... bleh!

> **IDontKnow9998 said:**
> It keep adding the 386.... The new and old 386.... Then It also adds the old K7... 

....

edit: On top of that, the updates wants 2 update the old 386...

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

> 
On top of that, the new K7 changes the path to (hd3,1) it should be (hd0,1)....bleh


## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

---

### Post by cosmicthoughts on 2006-07-20
Yeah I just had that same problem when I just installed new kernel. Did the hash thing and it's worked fine.

Don't forget you'll need to edit the file, rather than read only access you get via the GUI, run this in a terminal window.

```
sudo gedit /boot/grub/menu.lst
```

But you would be advised to create a backup file first.

---

### Post by cosmicthoughts on 2006-07-20
sorry, dbl post

---

