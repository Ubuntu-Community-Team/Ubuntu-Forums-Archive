---
title: "single user boot"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by jrev on 2008-01-06
Hi all,

My question is simple :

How do you start a single user boot on Ubuntu 7.04 or 7.10 ?

From the grub prompt I typed  :

grub> telinit 1 or 

grub> linux 1 

but the command are not recognized 

Could not find any practical answer to the question yet on this forum 

Thanks in advance

---

### Post by louieb on 2008-01-06
The easy way is to select the recovery mode  option from the GRUB menu.
From the grub prompt you need to enter root, kernel, and  initrd lines and will look something  similar to this: 

```

root   (hd0,0)
kernel  /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd   /boot/initrd.img-2.6.22-14-generic

```Of course the root partition, kernel name and initrd name  may vary depending on your installation.

---

### Post by jrev on 2008-01-06
Thank you Louis for this good answer.
Many speak about single boot but only a few can deal with it :)

---

