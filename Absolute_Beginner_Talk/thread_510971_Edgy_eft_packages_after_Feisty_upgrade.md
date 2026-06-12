---
title: "Edgy eft packages after Feisty upgrade"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by envykris on 2007-07-27
I have upgraded to Feisty Fawn from Edgy Eft using the Alternate CD. After the upgrade, i still see the Edgy Eft option on the GRUB loader, does that mean that the Edgy Eft packages and files are still occupying my HDD, if yes how do i remove those?

Cheers!

---

### Post by mikewhatever on 2007-07-27
Yes, Edgy's kernel should still be there. To remove it search for linux-image in synaptic, pick the right kernel, right click and select 'Mark for Removal'.

---

### Post by Seisen on 2007-07-27
You are talking aboutt the kernel, its best to leave that one on their so that if you have a problem in fiesty it makes it a little easier to fix. You can remove the old packages from Ubuntu if you want.

```
sudo apt-get autoclean
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by rich.bradshaw on 2007-07-27
What happens if you select EE and boot it?

Does it work?

You can delete the entry by editing

/boot/grub/menu.lst

(you need to be root to edit that file obviously!)

If it boots, then that's weird....

You can check what version you are in by looking at the help files on System.

---

### Post by envykris on 2007-07-28
i tried the auto-clean command...it dint have much to clean i guess, it exited almost immediately.  I tried the EE option, it doesnt boot, i think its the stale boot loader entry.

---

