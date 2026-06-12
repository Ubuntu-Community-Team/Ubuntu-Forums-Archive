---
title: "Old kernels"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-27
Is there a way to remove an outdated kernel? On my GRUB, I have two different Kubuntu's and two different recovery modes to choose from.

Nothing major, just curious.

---

### Post by moore.bryan on 2006-09-27
*it's a good idea to keep 1 or 2 for backup, but others can be removed from grub (edit menu.lst in /boot/grub) or completely (by deleting their images in /usr/src)...*

---

### Post by NetworkGuy on 2006-09-27
You can always edit your /boot/grub/menu.lst and remark out the entries for the kernel you don't want, or you can just turn the hiddenmenu back on and then you won't have to worry about the menu at all :)

---

### Post by klytu on 2006-09-27
> **Imsati said:**
> Is there a way to remove an outdated kernel? On my GRUB, I have two different Kubuntu's and two different recovery modes to choose from.

Nothing major, just curious.

You can easily remove the older kernels using Adept; it will update your GRUB menu automatically. As other posters indicated, there is no harm in leaving the older kernels and just removing them from the GRUB menu.lst or commenting them out; and at least one back up of an older working version can save you a lot of grief if your current one gets broken somehow.

---

### Post by Imsati on 2006-09-27
Good deal--thanks all!

I'll leave them, they're not doing any harm and it's only one previous kernel.

So, in simplest terms, keeping them on is like (pardon the reference) having a System Restore from XP?

--Jay

---

### Post by ewl1217 on 2006-09-27
>  So, in simplest terms, keeping them on is like (pardon the reference) having a System Restore from XP?

Not quite. XP's System Restore allows you to revert to a previous state with all installed programs (at least from my knowledge, since I've never had to use it myself). The older kernels only help if there's a problem with a newer kernel, but you're out of luck if any other upgraded programs have issues.

---

### Post by Imsati on 2006-09-27
Gotcha.

Much appreciated!

---

