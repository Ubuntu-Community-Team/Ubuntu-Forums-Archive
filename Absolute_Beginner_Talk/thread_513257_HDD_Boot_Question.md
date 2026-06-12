---
title: "HDD Boot Question"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by digital006 on 2007-07-30
I have two 200gb Hard Drives

The first one (Primary) has Win XP installed. The second (Slave) has Ubuntu installed on it. After a load of [problems](http://ubuntuforums.org/showthread.php?t=499356) I installed Ubuntu again and set grub to boot from hd1 (slave) which of course didn't boot. If I were to switch the drives so that my Ubuntu was primary and XP slave would grub pick up the fact that I have WinXP installed and allow me to log in through grub?

Cheers,
Mike

---

### Post by benx009 on 2007-07-30
can't you install grub to the mbr of your windows xp disk?  that should save you a lot of hassle.

---

### Post by digital006 on 2007-07-30
Unfortunately no because then it throws an Error 18 for the first time it boots then refuses to boot into grub after.

---

### Post by MQMike on 2007-07-30
I would have said what benX009 said – just re-install GRUB to the Windows drive MBR hd0 (and them maybe edit menu.lst to make sure Windows is correct).

If you do it your way, switching drives, you may get that to go, too, but Windows likes to be booted from the first (BIOS-) bootable hard drive, so in GRUB’s menu.lst, in the boot entry for Windows, you will have to use a map-dance.

This How-To would explain all these options.

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Read down through the posts following th first post until you come to the map dance thing – installing Windows to a non-first hard drive, dated July-something.)

---

