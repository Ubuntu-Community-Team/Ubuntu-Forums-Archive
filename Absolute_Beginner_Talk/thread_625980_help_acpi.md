---
title: "help acpi"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2007-11-28
Hi everybody

I have installed the ubuntu 7.10 on my laptop IBM thinkpad r40e. In the last version I had a lot of problem in the boot due to the acpi. When I start my pc, it stops the boot procedure. What can I do? How can I access to the kernel to change the acpi's properties?? Thank you very much

---

### Post by antonio_ing on 2007-11-28
Ok, now i'm inside ubuntu by means of the ubuntu cd. I put in the options acpi=off

Now what should I change in the linux kernel? where can I find the right file?

---

### Post by nick_h on 2007-11-28
You need to edit the file /boot/grub/menu.lst - and add your option to the line:
```
# defoptions=splash quiet
```
Then update grub by running:
```
sudo update-grub
```

---

