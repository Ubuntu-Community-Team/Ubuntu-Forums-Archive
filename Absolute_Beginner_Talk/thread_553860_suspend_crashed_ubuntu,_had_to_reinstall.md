---
title: "suspend crashed ubuntu, had to reinstall"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-09-18
so, i tried suspending my computer, put it in suspend mode. and the first partition of my harddrive got killed. it got rid of the bootloader, and there were tons of errors.   so how do i stop it from using suspend period?  i looked in the bios and i diddn't see a place to disable suspend. just all of acpi.  theres the options for s1 and s2  what do those mean?

---

### Post by por100pre1 on 2007-09-19
I disabled the suspend and hibernate buttons. I edited /apps/gnome-power-manager/can_suspend and /apps/gnome-power-manager/can_hibernate with gconf-editor. Hope it helps.

---

### Post by graigsmith on 2007-09-19
in gdm before you log in, there's still a button to allow standby mode after doing that.  is there any text file or anything that i can totally disable standby mode?

---

### Post by graigsmith on 2007-09-19
if i disable acpi in the bios, what all features get disabled in ubuntu?

---

### Post by graigsmith on 2007-09-20
anyone? theres still a suspend option on my gdm.  i am afraid to try it cause last time it wiped the first partition on my hard drive.

---

