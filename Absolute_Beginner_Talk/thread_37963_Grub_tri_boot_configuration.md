---
title: "Grub tri boot configuration"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by ehpmail on 2005-05-29
Please advise on the following configuration issue.

I've been running a dual boot with windows 2000 & xp.
Recently I installed ububtu linux and now have a tri boot.
I'm really only starting out with linux so I want the machine to start up with windows xp as the default operating system and not linux.
How do I configure the "grub" boot loader to boot with windows as default?

---

### Post by twisted_steel on 2005-05-29
You need to change the line ```
default		 0
``` in /boot/grub/menu.lst to another number. In my case, with Ubuntu and XP installed, this would probably be changed to a 3 since XP is the 4th item in the list (after ubuntu, ubuntu recovery mode, and memtest).

---

### Post by Mez on 2005-05-29
or, if you change ti to 

```
default saved
```

then when you select something in the mnu, it'll set that as the default until you choose to boot into something else... for example, if you select ubuntu, then you reboot, it'll auto-select ubuntu

but, if you then reboot and selct windows xp, next time you reboot, it'll select windowes XP automatically

---

