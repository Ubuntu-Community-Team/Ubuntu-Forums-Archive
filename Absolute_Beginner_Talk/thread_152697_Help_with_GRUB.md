---
title: "Help with GRUB"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by absintheparty on 2006-03-30
I have to add acpi=off to GRUB in order for Ubuntu to run on my laptop.  Anyone  know how to make that change perminant because now i have to do it everytime i start up.  Thanks

---

### Post by Mustard on 2006-03-30
Could you post your current menu.lst for grub?

```
sudo cat /boot/grub/menu.lst
```

---

### Post by meborc on 2006-03-30
be sure to turn acpi=off in BIOS as well!

---

### Post by johnnymac on 2006-03-30
You can add it as an option to your menu.lst in the grub directory so each time it boots it will be off.

---

