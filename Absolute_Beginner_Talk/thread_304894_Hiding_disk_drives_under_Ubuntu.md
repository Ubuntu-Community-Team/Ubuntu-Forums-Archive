---
title: "Hiding disk drives under Ubuntu"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-22
When Ubuntu boots up, it shows all my Windows drives on my desktop. I'd prefer to hide the boot drives, so they can't be accessed accidentally. Although I've found a couple of ways to hide them, they always come back again, next time I re-boot. Is there a way to hide certain drives permanently?

---

### Post by CatKiller on 2006-11-22
**gconf-editor**
/apps/nautilus/desktop/volumes_visible

Or mount those drives somewhere other than /media. /mnt might be a good option.

---

### Post by John E on 2006-11-23
> **CatKiller said:**
> **gconf-editor**
/apps/nautilus/desktop/volumes_visible

Thanks for the suggestion. I tried it - but unfortunately, it gets rid of all my volumes. I'd like to keep some of them but not others.

I suspect it might be safer if I just don't mount the relevant volumes. Is that possible?

---

### Post by Bachstelze on 2006-11-23
Yes, just open /etc/fstab in your favourite text editor and comment out (or remove) the lines regarding the drives you don't want mounted automatically at boot-time.

---

### Post by John E on 2006-11-23
It works HymnToLife. Thanks for the help. 8)

---

### Post by John E on 2007-10-08
Dunno if anyone here can help with this.... To maintain compatibility with someone else, I've had to install a 2nd version of Linux, called 64studio. Like Ubuntu, it's based on Debian and uses the Gnome desktop.

64studio's desktop has, at the top left-hand side, a 'Computer' icon that shows all the partitions on my hard drive - including the Windows ones. The Windows partitions don't actually get mounted (which is fine - because I don't want to mount them). But I'd prefer it if they weren't even shown. Somehow I've managed to set up Ubuntu so that it only displays my Linux partitions - but I can't remember how I did it. And I didn't get any replies when I posted this question on the 64studio forum. :(

Can anyone remind me how I decide which partitions get displayed (within the main 'Computer' icon) and which ones don't?

---

