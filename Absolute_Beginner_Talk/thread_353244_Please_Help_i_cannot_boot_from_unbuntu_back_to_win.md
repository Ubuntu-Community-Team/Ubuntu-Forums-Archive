---
title: "Please Help i cannot boot from unbuntu back to windows"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by UBnoob0403 on 2007-02-04
I installed Unbuntu and Windows XP on my laptop now that i have unbuntu installed on its own partition i dont know how to get my computer to boot to windows again when i need it....can someone please help...

---

### Post by dbbolton on 2007-02-04
> **UBnoob0403 said:**
> I installed Unbuntu and Windows XP on my laptop now that i have unbuntu installed on its own partition i dont know how to get my computer to boot to windows again when i need it....can someone please help...

do you have grub installed ?

---

### Post by annda on 2007-02-04
you should see a menu with boot options (it's called the GRUB menu) when you reboot the computer. or does it boot straight to ubuntu with no options?

---

### Post by kingmonkey on 2007-02-04
reboot computer, when grub comes (you might have to press esc to enter the menu) then select windows

---

### Post by UBnoob0403 on 2007-02-04
i can get to that GRUB but windows doesnt show up it only shows ubuntu...

---

### Post by Minyaliel on 2007-02-04
I had this problem too the first time I installed Ubuntu (honestly, I had no idea what I was doing). The reason was that I'd accidentally entirely erased Windows from my laptop. You're sure you didn't do this?

---

### Post by UBnoob0403 on 2007-02-04
i know i didnt delete it... it still shows up as a folder (WINXP) when im running ubuntu

---

### Post by annda on 2007-02-04
open the terminal (applications > accessories > terminal) and type:

```
sudo fdisk -l
```

post the output here so we can see if you still have windows

EDIT: too late again.

post the contents of your /boot/grub/menu.lst

---

### Post by kingmonkey on 2007-02-04
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu)

follow these directions

---

### Post by UBnoob0403 on 2007-02-04
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            3188        7112    31527562+   f  W95 Ext'd (LBA)
/dev/sda3            1276        2550    10241437+  83  Linux
/dev/sda4            2551        3123     4602622+  82  Linux swap / Solaris
/dev/sda5            3188        6374    25599546    7  HPFS/NTFS
/dev/sda6            6375        7112     5927953+   7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by annda on 2007-02-04
if you follow the instructions from the above link, use hda0,4 and not hda0,0 since you probably have windows on the sda5 partition, not sda1

---

