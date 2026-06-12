---
title: "Should I remove these items from my GRUB?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-19
I was looking at my GRUB entries, which looked like this:

```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot
``` 
can I take out the two entries with the outdated kernel versions (2.6.15-23-386) and just leave the newest version (2.6.15-25-386)?  What is that "memtest" entry all about?  Also, should I have a different kernel than the one seen above?  (I have an AMD Athlon XP 2800+ processor)

---

### Post by sailor2001 on 2006-06-19
[QUOTE=erik1397]I was looking at my GRUB entries, which looked like this:

```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot
``` 
can I take out the two entries with the outdated kernel versions (2.6.15-23-386) and just leave the newest version (2.6.15-25-386)?  What is that "memtest" entry all about?  Also, should I have a different kernel than the one seen above?  (I have an AMD Athlon XP 2800+ processor)[/QUOTE]
The consnsus I've seen is to hold onto the last outdated kernel for safety reasons...memtest checks the drive much like scan does in windows

---

### Post by user1397 on 2006-06-19
what about my third question? :D

---

### Post by Princey on 2006-06-19
[QUOTE=erik1397]what about my third question? :D[/QUOTE]


Unless you wanted the i686 Kernel, you're fine with what you have.

---

### Post by user1397 on 2006-06-19
[quote=Princey]Unless you wanted the i686 Kernel, you're fine with what you have.[/quote]so what's the advantage of i686 over i386 or the k# series kernels (like k6 or k7) ?

---

### Post by az on 2006-06-19
[QUOTE=sailor2001]The consnsus I've seen is to hold onto the last outdated kernel for safety reasons...memtest checks the drive much like scan does in windows[/QUOTE]

Well, keep it until you boot your new kernel and confirm it works.  Then, just remove the extra linux-image-XXXXXx packages using synaptic.  That will also take care of their grub entries.

As for 386 versus 686 or k7, you get a better optimisation and is more noticeable on low-end systems.

---

### Post by user1397 on 2006-06-19
[quote=azz]Well, keep it until you boot your new kernel and confirm it works.  Then, just remove the extra linux-image-XXXXXx packages using synaptic.  That will also take care of their grub entries.

As for 386 versus 686 or k7, you get a better optimisation and is more noticeable on low-end systems.[/quote]okay, i have the following packages installed in synaptic:

1) linux-image-2.16.15-23-386
2) linux-image-2.16.15-25-386
3) linux-image-386

Because I have an AMD Athlon XP processor, should I uninstall the above and install the following:

1) linux-image-k7
2) linux-image-2.16.15-25-k7

???

---

### Post by tonyr on 2006-06-19
**linux-image-xx** is a dummy container that pulls in the latest specific linux image package specified by **xx**.  You should keep at least one backup image, in your case
probably **linux-image-2.16.15-25-386**.

---

### Post by user1397 on 2006-06-19
[quote=tonyr]**linux-image-xx** is a dummy container that pulls in the latest specific linux image package specified by **xx**.  You should keep at least one backup image, in your case
probably **linux-image-2.16.15-25-386**.[/quote]i have decided to just remove the -23 package, and remain with the 386 and -25 packages.  i don't want to mess with any k_ packages, 386 works mighty fine for me!

---

