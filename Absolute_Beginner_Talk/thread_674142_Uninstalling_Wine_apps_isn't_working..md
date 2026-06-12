---
title: "Uninstalling Wine apps isn't working."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-21
So far I've had zero luck with using Wine; however I think that is probably just do to the specific apps (2) that I've tried to install and use.  Recently this morning I installed Photoshop CS2.  Aside from some slight oddities the install went through fine and I even loaded up the application twice without a problem; though I didn't try using it.  Instead I installed the 9.0.2 update and then I ran into the error:

[COLOR="Red"]"Unable to continue because of a hardware or system error. Sorry but this error is unrecoverable"[/COLOR]

So I figured I'd uninstall CS2 and try again.  Unfortunately I can't.  I've tried the Wine Application Uninstaller and the uninstall process *seems* to execute fine.  However once it's finished the program icons are still in the menu, the program files are still on the disk, and the program itself still attempts to execute when I launch it.

Does this sound familiar to anyone and, hopefully, does anyone know how to get around this?

---

### Post by skyjacker on 2008-01-21
> **toastysquirrel said:**
> So far I've had zero luck with using Wine; however I think that is probably just do to the specific apps (2) that I've tried to install and use.  Recently this morning I installed Photoshop CS2.  Aside from some slight oddities the install went through fine and I even loaded up the application twice without a problem; though I didn't try using it.  Instead I installed the 9.0.2 update and then I ran into the error:

[COLOR="Red"]"Unable to continue because of a hardware or system error. Sorry but this error is unrecoverable"[/COLOR]

So I figured I'd uninstall CS2 and try again.  Unfortunately I can't.  I've tried the Wine Application Uninstaller and the uninstall process *seems* to execute fine.  However once it's finished the program icons are still in the menu, the program files are still on the disk, and the program itself still attempts to execute when I launch it.

Does this sound familiar to anyone and, hopefully, does anyone know how to get around this?
Had the same problem... Don't no the answer, but would be interested in correcting.

---

### Post by toastysquirrel on 2008-01-21
> **skyjacker said:**
> Had the same problem... Don't no the answer, but would be interested in correcting.
I've scanned through Wine's user guide and Googled all over the place but so far the most comprehensive suggestion I've found boils down to uninstalling it through the uninstaller, or invoking "uninstaller" through the terminal... which does the exact same thing.

I imagine at some point in time there's been someone out there who's had this problem with Gutsy and Wine 0.9.53... I hope... :confused:

---

### Post by JeremyStein on 2008-01-21
If that's the only application you currently have installed in wine, you can just delete (or rename) your .wine directory.

---

### Post by toastysquirrel on 2008-01-21
Gah! :frown:

Okay, so I figured "what the hell" so I uninstalled Wine.  Then I reinstalled it.  Now I'm not sure how to get the shortcuts for the config and the GUI back because they're simply *not there* in the application menu.  After the uninstall of Wine, I removed the menu from the application menu (rightclick/edit); but I would think that wouldn't matter after the re-install.

Any thoughts?

---

