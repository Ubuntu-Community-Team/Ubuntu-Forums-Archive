---
title: "do i need grub with no boot options?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by smoker on 2006-10-21
hi, since getting a new harddrive, i have installed ubuntu as my only os (finally windoze gone for good!). as i no longer have to dual boot, can i uninstall grub so ubunto can load boot sequence quicker, or bypass grub?

at present, the grub screen appears for three seconds before booting unbunto. i know any boot time saved may be insignificant really, but it is annoying. if anyone can offer suggestions i will be grateful.

having a great time with ubunto, and on this forum,

thanks:D

---

### Post by sumguy231 on 2006-10-21
You will need grub to boot. You can, however, hide the menu. In a terminal, you can edit the Grub configuration file with: 
```

sudo nano -w /boot/grub/menu.lst

```
Find the line that looks like this:
```
#hiddenmenu
```

and remove the '#'
The menu will no longer display, but Grub will still wait about 3 seconds before booting. To reduce the time it will wait, find the line that looks like:
```
timeout  3
```
and reduce the number there to something lower. I hope that helps.

---

### Post by smoker on 2006-10-21
thanks, samguy,

i will try your suggestions,

cheers:)

---

