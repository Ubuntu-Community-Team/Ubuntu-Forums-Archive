---
title: "2 ubuntu's in grub since update."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Psyphre on 2007-02-16
Hi, yet another help thread from me (so many problems with ubuntu for some reason).
Anyway, after updating ubuntu yesterday, grub now shows another ubuntu option.

Ubuntu, Kernel 2.6.17-11-generic

The original one is:

Ubuntu, Kernel 2.6.17-10-generic

Why is there another one and what is the difference between the two?
Also what is really annoying is that my internet doesnt work on the new "Ubuntu, Kernel 2.6.17-11-generic", yet that has become the new default, so now i have to sit thru the whole boot process so i can manually select the old "Ubuntu, Kernel 2.6.17-10-generic".

Thx!

---

### Post by jezster on 2007-02-16
It's just the different Kernels, the top entry is the most recent one.  It's nothing to worry about as Grub, by default, always uses the entry in position zero (the first one) for booting.

As new Kernels are released new grub entries will be populated.  You can always edit the grub configuration and remove them.   /boot/grub/menu.lst

Cheers.

---

### Post by Tomosaur on 2007-02-16
The new one is the latest kernel version. Kernel updates are 'big' updates which upgrade the underlying operating system. The reason your internet connection doesn't work in the new update is because your net drivers were compiled into the old kernel, but the new kernel can't see them. You will need to either switch back to the old kernel, or repeat the steps you did to get your net connection working with the old kernel.

To make the old kernel the default, count which number it appears in the boot list. The first option is counted as 0, and the 'Other Operating Systems' line **is included** in the count. For example, if your old kernel is the third option down in the list, then the corresponding number is 2. You need to open up a terminal and enter the following command:
```

gksudo gedit /boot/grub/menu.lst

```

and look for a line which says 'Default 0'. Replace the 0 with the number you just counted, save the file, and reboot. The old kernel should now boot by default.

Alternatively, check the link in my sig.

---

### Post by milton1 on 2007-02-16
New kernels are added without deleting the old one, in case you need to switch back. You can delete whichever one you are not using with your package manager of choice. If you want to keep both for now, you can change the default in /boot/grub/menu.list

---

### Post by Psyphre on 2007-02-16
aaah i see, thanks guys! I reinstalled the drivers in the new kernel and it works!

---

