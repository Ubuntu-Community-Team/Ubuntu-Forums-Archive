---
title: "I killed windows again..."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by smithman89 on 2006-09-26
So, yes, this is now the second time i've killed windows trying to install Ubuntu 6.06.  But this time, there is a little catch...  The first time, on my home computer, i know what the problem is.  But i tried installing it on a computer in the school's computer lab(as a part of a Computer Club project).  Well, the problem is, that i dont even know what happened.  Ok, so the school computers have very small HDs, about 20gigs, and because there is only one HD per comp, and windows was already on it, i had to manually edit the partition table (for some reason, the "Use largest cont space" option wasnt there).  So, i re-edit the table, and i click next, and it comes to the screen that says "Do you want to do the following changes?".  I clicked no because ubuntu didnt take my numbers right for the manual edit.  So, i try this again (about  5 times), and then said screw it.  So i never fully completed the installation, nor did i ever accept the changes to be made.  Then, afterwards, we tried booting the computer up, trying to get to windows.  Well, now it says "Error loading Operating System".  Could anyone help me?  It seems very odd that i messed up windows without even installing ubuntu.

---

### Post by bulldog on 2006-09-26
If your windows still exist you can try to use the recovery console od a windows cd rom.

Boot the cd and get through the options till you reach install,repair or abort.
Take the repair option which brings you to a console with the existing windows install.

You have to log on with the administrator password and then try ```
fixboot
```

If this doesn't work do it all again and try then ```
fixmbr
```

If this fails I'm out of options.

---

