---
title: "refreshing grub boot loader"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-08-04
i recently uninstalled a second copy of ubuntut that i had on my second harddrive, but when i boot up grub boot loader still thinks it's there and says under other OS's ubuntu kernal( on hb2). is there a way i can refresh grub so that it is taken off?

Thanks much,
cptjaben

---

### Post by Tomosaur on 2006-08-04
EDIT: Woops, it's 'update-grub' instead sorry :P

---

### Post by cantormath on 2006-08-04
Did you try
```
laptop:~$ sudo update-grub
```

---

### Post by patrick295767 on 2006-08-04
> **cptjaben said:**
> i recently uninstalled a second copy of ubuntut that i had on my second harddrive, but when i boot up grub boot loader still thinks it's there and says under other OS's ubuntu kernal( on hb2). is there a way i can refresh grub so that it is taken off?

Thanks much,
cptjaben
 

go in /grub
check your grub conf

grub-install should also make it

---

### Post by richbarna on 2006-08-04
> **cptjaben said:**
> i recently uninstalled a second copy of ubuntut that i had on my second harddrive, but when i boot up grub boot loader still thinks it's there and says under other OS's ubuntu kernal( on hb2). is there a way i can refresh grub so that it is taken off?

Thanks much,
cptjaben

You probably still have it on the GRUB menu.list, do this to check :-

> gksudo gedit /boot/grub/menu.lst

Then just delete the entry for that partition

---

### Post by cptjaben on 2006-08-04
Thanks for all the help everyone.

cptjaben

---

