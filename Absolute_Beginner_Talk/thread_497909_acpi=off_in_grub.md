---
title: "acpi=off in grub"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by stepan2 on 2007-07-10
Hi guys . I recently compiled the latest kernel for my pc and realized that grub didnt have acpi=off enabled for it , sicne my pc will not boot with acpi=on.I am used to doing this with live-cd's but when i do this on my hdd isntall , it isnt like the livecd . maybe because it isnt isolinux. This is how the grub looks like ; 

title		Ubuntu, kernel 2.6.22-custom
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-custom root=UUID=2c69adc6-45c7-4f34-9e0e-f7a03f818175 ro quiet splash
initrd		/boot/initrd.img-2.6.22-custom
quiet
savedefault

where  do i add acpi=off?

---

### Post by stepan2 on 2007-07-10
i appologize but i must bump since in such  a short time i got one view and am going to the second page

---

### Post by logos34 on 2007-07-10
at the end of the 'kernel' line

...ro quiet splash acpi=off

or

 ...ro quiet splash noacpi

---

