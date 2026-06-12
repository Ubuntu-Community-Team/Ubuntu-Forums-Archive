---
title: "Actual grub menu is different from the one in menu.lst"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-27
I have just installed Kubuntu Feisty in a new partition. I was not able to bot from my hard disk until I figured out that I had to flag the right partition using the live CD.

I have 3 installs of Ubuntu in 3 different partitions. After booting, I opened my menu.lst and found out that the one in my menu.lst is different from the actual grub menu that I saw. I think it is the case because I have many installs of Ubuntu in different partitions.

How can I manage to edit my grub menu now if the menu.lst that I access is different from the actual grub menu?

---

### Post by canadianwriterman on 2007-04-27
What's happened is that the bootup GRUB menu is fed by the very last install you made. There will be a menu.lst file in each of your Ubuntu installs. So, the one you checked out and saw that was different is probably one from of your other installs. To change the bootup menu, edit the menu.lst file from your last install.

---

### Post by phidia on 2007-04-27
I've had several installs of ubuntu/different partitions. Presently i just have edgy and feisty. I usually install the "extra" ubuntus with grub installed to the root partition so that I can use the chainloader command to hand the boot over to the grub for that install.

But you haven't specified how the menu.lst is different from your grub menu. Maybe post a screen shot of the grub boot menu and your menu.lst and someone here can sort it out?

---

### Post by paparucino on 2007-04-27
> **wersdaluv said:**
> 
How can I manage to edit my grub menu now if the menu.lst that I access is different from the actual grub menu?

Suppose I want to boot from hdb3 while now your machine boots from hdb6

Modify /boot/grub/menu.list on hdb3 introducing all the OS you have on your machine and from which you can boot.
Then open a terminal

```

$ grub
grub>find /boot/grub/stage1 
grub>root (hd1,2)      (where hd1 is your second disk, 2 is 3-1 since it counts from 0)
grub>setup (hd0)       (write grub on MBR in the first HD)
grub>exit
$ reboot
 
```
Enjoy yourself :-)

---

