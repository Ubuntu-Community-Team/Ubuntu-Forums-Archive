---
title: "kernel boot options"
date: 2006-09-19
forum: Apple PPC Users
---

### Post by steven43126 on 2006-09-19
To boot at the moment i have to add the noapic option, probably because this is a fairly new am2 motherboard and it isn't properly supported yet. My question is where is the correct place to put the noapic option, i recently had it set in grub.conf but it got overwritten with the upgrade to a new kernel? is this the correct place or do i have to check this file every time i upgrade to a new kernel version?

many thanks steve.

---

### Post by nullmind on 2006-09-19
My girlfriend has the same issue and uess the noapic option. You can add option as an argument to the kernel line in the grub boot entry, like this:

```

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash **noapic**
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

```

That's my menu.lst entry for ubuntu using the 686 kernel, yours is likely different and has a different partition so don't copy it line-for-line. I bolded the only change you should need to make.

When you boot you can press E to edit the boot for this boot only and apply those changes (press B to boot after you edit the lines). To make the changes permanent just edit /boot/grub/menu.lst (back it up first). If your kernel was updated there may be a backup of the menu.lst that has your old configuration in it.

---

