---
title: "Dual Boot (Grub) Question"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-11-11
I have Vista and Fiesty set up as a dual boot--Vista on hda and Fiesty on hdb with grub on the MBR of hda.
Grub boots both just fine.
Now I wanted to install Fedora-8 on hdb next to Fiesty.
If I put the Fedora bootloader(Grub) in the Fedora root partition on hdb, will it boot ok from the hda MBR or do I need to do something else ?
Thanks for any guidance..

---

### Post by taurus on 2007-11-11
Why not just install GRUB from F8 to MBR--/dev/hda.  Then, it will boot F8, Ubuntu, and XP.

---

### Post by Milt888 on 2007-11-11
> **taurus said:**
> Why not just install GRUB from F8 to MBR--/dev/hda.  Then, it will boot F8, Ubuntu, and XP.

That sure would be the easiest for me..
Would I need to do anything about the Ubuntu grub thats already in the MBR before I install the other one ?

---

### Post by mahiyar on 2007-11-11
Is Fedora going to stay long term? Then and only then it would be worthwhile to link grub with f8 else you are happy sticking with your original plan. If you decide grub should be f8's you wont have to do anything, hopefully fedora will recognise the other oper sys. (never worked with fedora but grub behaviour should be same). However take care to point to the correct hard disk while installation.

---

### Post by Milt888 on 2007-11-11
> **mahiyar said:**
> Is Fedora going to stay long term? Then and only then it would be worthwhile to link grub with f8 else you are happy sticking with your original plan. If you decide grub should be f8's you wont have to do anything, hopefully fedora will recognise the other oper sys. (never worked with fedora but grub behaviour should be same). However take care to point to the correct hard disk while installation.

Thank you. I guess my question was; whether fedora would boot from the ubuntu grub or not.

---

### Post by mahiyar on 2007-11-11
That would not be too difficult to set up, when you install f8 dont install grub with it. Then set up something like this in your menu.lst of your Ubuntu.

title         Fedora Core 8
**root        (hd0,5)**
kernel         /vmlinuz root=/dev/**sdb6** ro quiet splash
initrd         /initrd.img
quiet
savedefault
boot

What I have marked in bold could change as per where you have installed fedora. If you want to know more about grub this site will help [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Milt888 on 2007-11-12
> **mahiyar said:**
> That would not be too difficult to set up, when you install f8 dont install grub with it. Then set up something like this in your menu.lst of your Ubuntu.

title         Fedora Core 8
**root        (hd0,5)**
kernel         /vmlinuz root=/dev/**sdb6** ro quiet splash
initrd         /initrd.img
quiet
savedefault
boot

What I have marked in bold could change as per where you have installed fedora. If you want to know more about grub this site will help [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Thanks to you and Taurus, I think I have it sorted out now.
I just let the Fedora grub install in the MBR and it boots all three now.
Thanks for the help.

---

