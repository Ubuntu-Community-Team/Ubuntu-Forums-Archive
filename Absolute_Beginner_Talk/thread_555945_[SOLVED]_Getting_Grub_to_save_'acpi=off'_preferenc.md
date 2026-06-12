---
title: "[SOLVED] Getting Grub to save 'acpi=off' preferences"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-09-20
How do you force Grub to make sure it adds 'acpi=off' to the end of every kernel after running 'update-grub'?

I have them above the AUTOMAGIC KERNELS LIST and commented below like so:

> defoptions=quiet splash acpi=off

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

...

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=off

However, whenever I run 'update-grub', the kernel alternatives always say 'quiet splash' without my 'acpi=off' flag.

Can anyone help?

---

### Post by Pumalite on 2007-09-20
Edit your menu.lst and add them to the end of the 'kernel' line.

---

### Post by dcstar on 2007-09-20
> **altonbr said:**
> How do you force Grub to make sure it adds 'acpi=off' to the end of every kernel after running 'update-grub'?

I have them above the AUTOMAGIC KERNELS LIST and commented below like so:
......
However, whenever I run 'update-grub', the kernel alternatives always say 'quiet splash' without my 'acpi=off' flag.

Can anyone help?

It looks ok (and I use that area and it works on my kernel updates), I suspect it is the "=" character, is there an alternative command string for turning ACPI off? (like "noacpi"?).

---

### Post by altonbr on 2007-09-21
> **Pumalite said:**
> Edit your menu.lst and add them to the end of the 'kernel' line.

That erases after every 'update-grub'. I always have to set that manually. I'm looking for it to automatically append 'acpi=off'. This is for one of my clients and I can't afford to have her always come over for a fix on a kernel update.

> **dcstar said:**
> It looks ok (and I use that area and it works on my kernel updates), I suspect it is the "=" character, is there an alternative command string for turning ACPI off? (like "noacpi"?).

I'll take a look. I think 'update-grub' DID append 'acpi=off' this time. I would say a reboot fixed it, but that wouldn't make any sense.

---

