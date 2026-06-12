---
title: "Help with VP2007"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by J_VMPC on 2008-01-06
well Linux just won't install on my hard drive unless I install it on my current OS therefore erasing it and everything prior to the installation
so i decided to install linux on a Virtual PC 
this has been very helpful  [https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004#head-5042494ef5944405cc2090cabffa7f5faa16f349](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004#head-5042494ef5944405cc2090cabffa7f5faa16f349)

but i can't seem  to get the mouse support to work
ive tried this 
   1.      At boot press the Esc key enter the grub menu screen.
   2.      Make sure your kernel boot line is selected.
   3.      Press e to edit the kernel boot line.
   4.      Type i8042.noloop at the end of the line.
   5.      Press enter to accept the changes and then b to boot.
   6.      Once logged into Ubuntu, open the /boot/grub/menu.lst as root.
   7.      Add i8042.noloop to the end of the kernel boot lines.
but after that ubuntu just won't load
am i entering the i8042.noloop in the right spot? where should i then?

---

### Post by J_VMPC on 2008-01-06
when i click esc in GRUB 
i have 3 options... normal, recovery mode, and memtest...which one should i choose
i choose normal since i already used recovery mode to fix the display issue
so now i have the choices root, kernel, initrd and quiet....i tried putting the code in kernel but that just causes ubuntu to not load...same when i tried it in root

what should i do? what am i doing wrong?

---

### Post by J_VMPC on 2008-01-07
anyone know what to do? should this be in another forum?

---

### Post by sonofusion82 on 2008-01-07
alternatively, perhaps you could try using wubi.
i have not tried that myself, but some guys here might be able to give u some advice on that.

I have used VPC 2007, but mostly for Microsoft OSes as they don't really support Linux, but it sometimes. I have tried knoppix live CD with VPC 2007.

---

