---
title: "Deleting old linux kernels"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by grontoft on 2006-09-14
Hi, just a quickie:

Can i delete old kernels that i don't use anymore??:tongue:

---

### Post by Kilz on 2006-09-14
> **grontoft said:**
> Hi, just a quickie:

Can i delete old kernels that i don't use anymore??:tongue:

Yes you can. In synaptic they are listed as linux-image packages. That will also remove the listing in grub. I do recommend leaving the 2 most currect ones. just mark them for removal and hit apply.

---

### Post by Metacarpal on 2006-09-14
Yep.

If you know the exact version number string, you can do it in terminal (Applications > Accessories > Terminal):
```
sudo aptitude remove linux-image-2.16.*##-##-ARCH*
```
using the correct replacements for ##-##-ARCH, of course

Alternately, you can use Synaptic (System > Administration > Synaptic).  Either search for "linux" (without quotes) or just scroll down 'til you see what you're looking for.

NOTE: only remove packages marked with the specific version number you want to remove.  Do not remove packages like linux-386.

---

### Post by grontoft on 2006-09-14
can I delete something like this:

linux-image-2.6.12-10-386

---

### Post by xpod on 2006-09-14
WOW....that was spooky........just as i was reading your post about deleting that kernal i got flashed with an update for the exact same one....

....Oh and now i must restart:roll: ....now i bet you cant just "consider" your updates in any windows OS and have them appear just like that:p 

Great feature.....:rolleyes:
EDIT:okay slightly different version but still

---

### Post by max.diems on 2006-09-14
If it helps, I asked this question [earlier today]("http://www.ubuntuforums.org/showthread.php?t=257271").

---

