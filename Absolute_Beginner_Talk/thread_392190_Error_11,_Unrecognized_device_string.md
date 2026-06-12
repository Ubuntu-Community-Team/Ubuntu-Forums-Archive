---
title: "Error 11, Unrecognized device string"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by patientjob on 2007-03-24
Hello everybody,
after updating my ubuntu partition i had to restart so the changes will take effect. From that time every time i try to boot at an ubuntu option at the GRUB menu i receive the message "Error 11, Unrecognized device string". On the other hand i can boot without any problem in my windows partition :confused: . Any ideas about how i will be able to resolve this??

---

### Post by deejaykaybee on 2007-03-24
I have the exact same problem here.  

It seems there is a way to edit grub from the grub menu (without actually booting into any OS).  I can see the hard drive mappings this way, so I am wondering if you can used this to fix the error.

thanks

---

### Post by patientjob on 2007-03-24
It seems that i found a way resolving the problem. Primarily with "sudo fdisk -l" i found that my linux partition (from where i boot) is /dev/sda2. Then i checked with "gksudo gedit /boot/grub/menu.lst" my menu.lst. For some strange reason at the sequence "title-root-kernel-initrd" etc there was no parenthesis at the end of (hd0,1) that coresponds at the root field. Also in the kernel option  the "root=/dev/sda.." was pointing at the wrong partition (instead the one i found with sudo fdisk -l). Therefore i changed the menu.lst with the correct data and everything returned to normal.
Hope it will help anybody else with a simiral problem.

---

