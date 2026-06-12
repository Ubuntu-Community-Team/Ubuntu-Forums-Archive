---
title: "Changing OS Boot Order"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Ben Stamper on 2006-02-03
Is it possible to change the boot order in the startup screen? Say, put Ubuntu in front of Debian? Thank you.

---

### Post by gw90se on 2006-02-03
You can edit the grub menu, but back it up first!
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Leo_01 on 2006-02-03
> Of course it is. The file you need to edit is /boot/grub/menu.lst.

There are a group of several lines (starting with a title line) for each boot option. You can move there groups around to change the order. You can comment out or delete groups you don't want to see. You can add other groups if you want to triple-boot.

Beware that stuff inside the AUTOMAGIC KERNELS LIST will get overwritten every time the kernel is updated. But I usually comment out the recovery mode and memtest options after a few days, and change the title of the main Ubuntu entry, just to make the boot selection screen look neater. Mine just says
Quote:
Linux
Windows

You can change the defaut entry by changing the line default 0 near the top, but I prefer to change the order and leave the top entry (0) as the default.

by : steve.horsley taken from my topic.

---

