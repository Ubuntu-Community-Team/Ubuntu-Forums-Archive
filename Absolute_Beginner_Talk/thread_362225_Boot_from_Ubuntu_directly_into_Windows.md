---
title: "Boot from Ubuntu directly into Windows"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Hasen_A on 2007-02-15
Hi, I want to boot from Ubuntu directly into Windows without going into the boot menu, where Ubuntu is my default OS to boot. I still want to have my dual boot active when I reboot normally. Is there a command on how to boot directly?

following didnt work under grub as sudo:
```

grub> root (hd0,0)
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
```

---

### Post by jpeddicord on 2007-02-15
`grub-reboot <entry#>` in the terminal should do the trick. Entry# is the menu item number. If it is the first item, then it will be 0, second=1, third=2, etc. You could put Windows above Ubuntu in the menus so that grub-reboot 0 will always work.

---

### Post by lamalex on 2007-02-15
> **jacobmp92 said:**
> `grub-reboot <entry#>` in the terminal should do the trick. Entry# is the menu item number. If it is the first item, then it will be 0, second=1, third=2, etc. You could put Windows above Ubuntu in the menus so that grub-reboot 0 will always work.

wow that's a handy trick. i never even thought of doing this.

---

### Post by Hasen_A on 2007-02-15
thanks a bunch

---

### Post by Hasen_A on 2007-02-17
> **jacobmp92 said:**
> `grub-reboot <entry#>` in the terminal should do the trick. Entry# is the menu item number. If it is the first item, then it will be 0, second=1, third=2, etc. You could put Windows above Ubuntu in the menus so that grub-reboot 0 will always work.

grub-reboot 0 didn't work, on reboot the boot menu came up and it was on the default value 1 for ubuntu again. what also bothers me: everytime i do "sudo grub-reboot 0" grub gets messed up and I receive the error message 18 on boot menu selection.

A simple
```
sudo grub-install --root-directory=/ /dev/sda
``` fixes this and I am able to boot Ubuntu normally again.

---

