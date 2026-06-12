---
title: "help to recover ubnutu where is my ubuntu"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-09-18
I had duel boot winxp & ubuntu 7.4.
 Over this I installed PClinuxos KDE.
Now I lost Ubuntu.but winxp is there.
 How to recover it.Please help me. THANKS:(

---

### Post by conehead77 on 2007-09-18
cant you choose ubuntu from the bootmenu anymore?

post the output of 
```
cat /boot/grub/menu.lst
```

---

### Post by drpas2k on 2007-09-18
> **conehead77 said:**
> cant you choose ubuntu from the bootmenu anymore?

post the output of 
```
cat /boot/grub/menu.lst
```

This is the result. please help. thanks

[root@localhost ~]# cat /boot/grub/menu.lst
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,2)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda3  acpi=on splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title linux-nonfb
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hda3  acpi=on
initrd (hd0,2)/boot/initrd.img

title failsafe
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hda3  failsafe acpi=on
initrd (hd0,2)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1
[root@localhost ~]#

---

### Post by conehead77 on 2007-09-18
you need to add a entry for ubuntu (i assume "linux" will boot the PClinux?)

it seems that ubuntu is on (hd0,1), so you could try to add sthg like this code:

```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4fa60d9a-d5c3-4e03-9edd-e097baef7ad7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
```

just paste it above or under the other entries. make sure you have the 2.6.20-16 kernel. if not, you need to change this part of the code.
i think you can look at your ubuntu partition in the /boot/ directory for your version of the kernel. If the above isnt correct, you will get a error message, but still can boot into XP, etc.

but i recommend to backup the menu.lst before changing it anyways.

---

### Post by drpas2k on 2007-09-18
> **conehead77 said:**
> you need to add a entry for ubuntu (i assume "linux" will boot the PClinux?)

it seems that ubuntu is on (hd0,1), so you could try to add sthg like this code:

```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4fa60d9a-d5c3-4e03-9edd-e097baef7ad7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
```

just paste it above or under the other entries. make sure you have the 2.6.20-16 kernel. if not, you need to change this part of the code.
i think you can look at your ubuntu partition in the /boot/ directory for your version of the kernel. If the above isnt correct, you will get a error message, but still can boot into XP, etc.

but i recommend to backup the menu.lst before changing it anyways.

Where to add? I am new to linux. 
 how to backup the menu.
Please help me.

---

### Post by conehead77 on 2007-09-19
backup the file:
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst

enter the root-password and you created a backup file "menu_backup.lst"

insert the code i posted:
gksudo gedit /boot/grub/menu.lst

the text editor will appear and you can copy/paste it just before the line with "title linux"

save the file and reboot. you should be able to boot into ubuntu now

---

