---
title: "Grub replacement"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2007-04-20
Is there a replacement for grub? I dunno what it is, but I just don't like how Grub is laid out. Or maybe I just want something more graphical, I don't know.

Are there any replacements I can stick in after-install?

---

### Post by kabanta on 2007-04-20
I would also like to know whether there is a graphical alternative to GRUB.

My plan is to install Feisty on my mother's machine which will also have XP. I would like to have something a little less intimidating for her when she chooses between booting into Feisty or XP.

---

### Post by eyelessfade on 2007-04-20
No there isn't you have lilo, but its much the same as grub (graphic wise).

On the other side the bootloader must be minimalistic since it shall work always on all hardware. And small since it lives on the bootblock.  The windows bootloader is on the otherhand even more primitive. Everyone have seen the two/tree alternatives. "Boot normal, boot in savemode"

---

### Post by kabanta on 2007-04-20
> **eyelessfade said:**
> No there isn't you have lilo, but its much the same as grub (graphic wise).

On the other side the bootloader must be minimalistic since it shall work always on all hardware. And small since it lives on the bootblock.

Ah, that makes sense. Well, one option is for me to edit the GRUB menu so it is just two choices for her. The problem is that certain package updates will automatically change the GRUB menu. Is there any way to avoid this?

---

### Post by cypherzero on 2007-04-21
Reinstall GRUB and get it to point to a different settings file location.

Bootloaders are rarely graphical - they have to fit into that tiny space at the start of your hard drive.

There is a version of GRUB which displays a splash image though.

---

### Post by kabanta on 2007-04-21
> **cypherzero said:**
> Reinstall GRUB and get it to point to a different settings file location.

Ah! Good idea. thanks.

---

