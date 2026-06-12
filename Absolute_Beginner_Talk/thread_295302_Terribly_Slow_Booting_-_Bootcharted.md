---
title: "Terribly Slow Booting - Bootcharted"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ollienz on 2006-11-07
After upgrading from Dapper to Edgy, everything works a treat, except for there being random huge pauses in the boot process, especially one directly after starting metacity. I have no idea what is causing this. Any ideas?

Pls note: Bootchart is attached.

---

### Post by garethc on 2006-11-07
I have the same problem on my Inspiron 6400 laptop under Edgy - at least in graphical bootup it pauses about halfway through loading for about 30 seconds. Strange.

---

### Post by cimas on 2006-11-18
Hello
 The same think here for Toshiba satellite under ubuntu. On beggining I had problems with booting and shutting down the system, but shutting down problem was fixed with changes in boot/grub/menu.lst (#defoptions=quiet splash [COLOR="Red"]acpi=force [/COLOR]) and /etc/kde3/kdm/kdmrc ( [X-:*-Core] [COLOR="red"]TerminateServer=true[/COLOR]). But booting problem is still there :(. The "progression bar" is stuced somewere in the middle for around 1 min. If anybody have the same problem or know the solution, please replay :)

---

