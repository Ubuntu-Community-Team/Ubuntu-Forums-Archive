---
title: "Dual booting"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-06-16
ok i have this on a slave and my xp on master i cant get xp in the list of os in grub can anyone tell me what is wrong thanksero1337.
You last visited

---

### Post by FleetAdmiral74 on 2007-06-16
please do a quick search on editing grub, this has been asked many times before.

---

### Post by arvevans on 2007-06-16
The file you need to look at, and possibly edit, is /boot/grub/menu.lst

Make a backup first so you can recover if a mistake is made.  Use sudo with a text editor to make any changes.

You should see a boot stanza for Linux and another for Microsoft.  By changing the "default number" setting, or by changing the order of these stanzas, you can control which system boots by default.
_._

---

### Post by starcraft.man on 2007-06-16
Ok... I don't think those posts were exactly helpful.

[Here is a complete how to explaining all of the functions of GRUB ]("http://users.bigpond.net.au/hermanzone/p15.htm")and how to edit the menu list so that XP boots properly. Read it from top to bottom and if you have any questions ask, it doesn't give you exact instructions but IMO its more important to understand what your doing rather than simply getting a packaged answer that fixes it. Do remember to always back up the menu.lst file before editting (and date or number the backups sequentially) so you can restore from live cd if theres a problem.

Oh and to copy and backup its good to know the basic terminal functions [found here.]("http://www.linuxcommand.org/lts0050.php") Linux command is an excellent resource for learning terminal.

---

