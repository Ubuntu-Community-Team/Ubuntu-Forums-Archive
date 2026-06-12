---
title: "viewing grub menu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-07-09
my friend wants to install ubuntu(he already has XP) so before installing he wants to save his grub menu how should one do this.

---

### Post by reset3x on 2007-07-09
XP has no GRUB menu..

---

### Post by UnixAnt on 2007-07-09
Perhaps not the best way, but I would simply back up the following file:

/boot/grub/menu.lst

To a convenient location.  If you need the contents post-install you could combine the 2 menu.lst files, or overwrite one with the other, or whatever.

I'm sure there is a less crude method, however.

---

### Post by starcraft.man on 2007-07-09
> **pardesi said:**
> my friend wants to install ubuntu(he already has XP) so before installing he wants to save his grub menu how should one do this.

Huh? Why would he have the GRUB bootloader installed when he's only got XP? If you mean save the existing MBR, bleh its no big loss. If he's got the original install CDs he can probably just use the FIXMBR command. GRUBs a superior bootloader anyway...

If he wants to ensure he's still bootable even without Ubuntu, you can always tell him how to make a /boot partition separate from the install then if he gets rid of Ubuntu he can keep using GRUB. I wouldn't worry about it.

Oh and if he seriously botches the install, make sure he has a [GAG disk]("http://gag.sourceforge.net/"). Will instantly make him bootable again, with no trouble.

---

