---
title: "Adding second distro to GRUB"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-11-16
I have Ubuntu on partition 1 and Ubuntu swap on partition 5. Now I have installed Gentoo on partition 2. I did not choose grub as an option during the Gentoo install, because I knew I could just configure my Ubuntu grub instead.

Now my question is how do I configure grub? 

Edit: I think I have it partially figured out. I added this entry to my /boot/grub/menu.lst

```
title           Gentoo
root            (hd0,1)
kernel          /boot/kernel-genkernel-x86-2.6.17-gentoo-r7
initrd          /boot/initramfs-genkernel-x86-2.6.17-gentoo-r7
boot
```

It seems to start loading Gentoo but than gives an error about boot device. I think I will try the Gentoo forums to ask about this.

---

### Post by lloyd_b on 2006-11-16
You probably need a "root=/dev/hda2" on the "kernel" line (assuming that hda2 is the correct partition, of course).

Lloyd B.

---

### Post by bodhi.zazen on 2006-11-16
> **lloyd_b said:**
> You probably need a "root=/dev/hda2" on the "kernel" line (assuming that hda2 is the correct partition, of course).

Lloyd B.

kernel  /boot/kernel-genkernel-x86-2.6.17-gentoo-r7 root=/dev/hda2 ro 

You can also add splash and quiet if you like.

---

