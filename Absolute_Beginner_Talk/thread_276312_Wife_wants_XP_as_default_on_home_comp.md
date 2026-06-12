---
title: "Wife wants XP as default on home comp"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-12
Hey all. Until I've got all of the bugs worked out of my brain and my work comp, the wife wants to be able to turn on the home comp and see XP and nothing but. Right now, as I'm sure you can guess, there's a small time delay to select which OS you want, and if you're not standing there watching, Dapper loads by default. How do I change the default OS to XP? TIA.

---

### Post by Kateikyoushi on 2006-10-12
Have to edit your grub menu.
Can do it in a minute, just follow [these steps.]("http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu")

---

### Post by JayTee on 2006-10-12
Here's a link to a good how-to on dual-boot configuration. If dual boot is already setup all you need to do is edit your /boot/grub/menu.lst file to add the statement savedefault before the line that says chainloader +1 in the section that boots XP. That should do it.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by taurus on 2006-10-12
Boot up Ubuntu and long in with your username and password.  Then, you need to edit /boot/grub/menu.lst and change the default from 0 to whichever entry is for Windows.  To edit /boot/grub/menu.lst, open a terminal, Applications -> Accessories -> Terminal, and type

```

gksudo gedit /boot/grub/menu.lst

```
Now, look in there to see which entry is Windows.  Remember, the first one counts as zero so if Windows is the fifth entry on that list, then change the value to 4...

```
default         4
```
Save it and reboot.

---

