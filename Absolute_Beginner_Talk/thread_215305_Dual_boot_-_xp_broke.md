---
title: "Dual boot - xp broke"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by maiden30403 on 2006-07-13
Ok I've finally got ubuntu working great but unfortunatly I need xp for some apps. But my xp partition messed up on install and I didn't catch this before so now I have my linux partition working fine but my xp partition is screwed so is there any way of re-installing xp without it effecting grub?

---

### Post by BigDave708 on 2006-07-13
Probably not. Windows XP doesn't play nice with other operating systems. When you install it, it wipes the MBR and sticks only itself back in the MBR. The easier way to dual-boot is to install XP first and then install Ubuntu on another partition. That way, at worst, all it takes is a little tweak with GRUB in Ubuntu to allow you to boot XP. 

I don't know about this, but it may be possible to re-install Windows and allow it to pollute the MBR and then use [FS Driver]("http://fs-driver.org/") to edit GRUB once you are logged into XP.

Apart from that, I haven't got a clue :oops: . . .

---

### Post by cstudent on 2006-07-13
This might help;

[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)

---

