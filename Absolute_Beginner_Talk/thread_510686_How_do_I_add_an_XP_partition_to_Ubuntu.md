---
title: "How do I add an XP partition to Ubuntu?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by babya on 2007-07-26
I have Ubuntu Studio installed and want to add Win XP* for a dual boot.  What's best way to go about doing this?  Can I add XP without having to do a clean install of Ubuntu again?



(*I just do.)

---

### Post by oilchangeguy on 2007-07-26
you can set up xp as a virtual machine. or you can install xp, and reinstall grub (it's best to install windows first, then ubuntu).

---

### Post by dangerpl on 2007-07-26
In my experience it was much easier to start fresh, and installing Windows first... Grub had no problem finding windows... But that's just me, I'm not an expert... I'm pretty sure there's a way to install windows, but if i'm not mistaken you would have to manually configure grub...Good luck! Just adding my few words...

---

### Post by babya on 2007-07-26
That's what I thought, best to install XP first.  No biggy.  Just thought I'd make sure.  Thanks.

---

### Post by paradoxchild on 2007-07-26
Make sure you partition room for ubuntu and xp, much better to do xp first becuase it installs its own bootloader, and you'd have to reinstall grub if you install xp after ubuntu.

---

