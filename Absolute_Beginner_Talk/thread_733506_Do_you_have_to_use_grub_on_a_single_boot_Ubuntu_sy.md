---
title: "Do you have to use grub on a single boot Ubuntu system?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-23
Basically that's it.
If I want to install Ubuntu only on my computer do I still have to have Grub installed to boot from the HD? I'm not talking about any third party boot loaders, just a stictly Ubuntu install.  This is not a real problem but more for information right now.

---

### Post by smartboyathome on 2008-03-23
Technically you would have to have something to boot up ubuntu. You can set it to not show grub and have to press esc in a certain time limit to show it by enabling hiddenmenu in /boot/grub/menu.lst, which should be like it isn't there.

---

### Post by jken146 on 2008-03-23
I believe that you do.  As I understand it, the BIOS looks to the MBR of the first boot device (you can change this in the BIOS setup).  Whatever is there (GRUB stage 1) points to something else in another place (GRUB stage 2, in /boot) which then runs whatever is necessary for your OS to start (there is a menu.lst file that tells GRUB stage 2 where the kernel is).

It is very useful to have GRUB around if something breaks -- that way you can get into Recovery Mode quite easily.

---

### Post by forrestcupp on 2008-03-23
You have to have a boot loader, and this is the default one, so you're better off not messing with it.  But to make it invisible, do what smartboyathome said.

> **smartboyathome said:**
> Technically you would have to have something to boot up ubuntu. You can set it to not show grub and have to press esc in a certain time limit to show it by enabling hiddenmenu in /boot/grub/menu.lst, which should be like it isn't there.

To do that, type in a terminal
```
gksu gedit /boot/grub/menu.lst
```
delete the '#' that is in front of 'hiddenmenu' to make it not show the menu.  You can also change the number after 'timeout' to be something small.  That is the number of seconds before it automatically boots to the default choice.  I'd leave at least 2 seconds to give yourself time to hit escape to boot to the recovery mode if you need to.

After making these changes, save it and next time you boot, you won't see the menu and it will take less time to boot the default choice.

---

### Post by garyed on 2008-03-23
Thanks for the replies,

I like the way grub handles multi-boot systems but I was curious if there was another option on single boot systems.

---

### Post by jken146 on 2008-03-23
There are other bootloaders (e.g. LILO) but they all do the same thing really.

---

### Post by louieb on 2008-03-23
You have a choice. You don't have to use GRUB but you do need a boot loader.
[Boot loader showdown: Getting to know LILO and GRUB]("http://www.ibm.com/developerworks/linux/library/l-bootload.html#N102C4")

And there are some others. check the Dual Boot link in my signature.

---

### Post by forrestcupp on 2008-03-24
> **garyed said:**
> Thanks for the replies,

I like the way grub handles multi-boot systems but I was curious if there was another option on single boot systems.

Even the Windows boot loader does the same thing if you dual boot with 2 versions of Windows.  They all pretty much do the same thing, only with different interfaces and structures.

---

