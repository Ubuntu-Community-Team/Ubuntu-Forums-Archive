---
title: "Triple-boot issues (XP, OSX, Ubuntu) on a MBP 3.1 NEWBIE"
date: 2008-08-04
forum: Apple Hardware Users
---

### Post by OzzyBuntu on 2008-08-04
Hey fellas,
im having problems booting windows after installing ubuntu Hardy. Everytime i choose Windows XP from rEFIT boot menu, OSX boot menu (from bootcamp) and GRUB, it starts loading, but it reboots before showing anything else. A blue screen with text appears, but its too quick to tell what the error is... Im using a MBP 3.1 Santa Rosa with OSX 10.5.4
Has anyone encoutered this problem?
I have windows partition completely backed up, so im not worried about any missing files.
Thanks

---

### Post by cyberdork33 on 2008-08-04
> **OzzyBuntu said:**
> Hey fellas,
im having problems booting windows after installing ubuntu Hardy. Everytime i choose Windows XP from rEFIT boot menu, OSX boot menu (from bootcamp) and GRUB, it starts loading, but it reboots before showing anything else. A blue screen with text appears, but its too quick to tell what the error is... Im using a MBP 3.1 Santa Rosa with OSX 10.5.4
Has anyone encoutered this problem?
I have windows partition completely backed up, so im not worried about any missing files.
Thanks
That would be the Blue Screen of Death. However, by default, Windows is set to automatically reboot on such an error (which is really very helpful for problem diagnosis :rolleyes:).

Windows generally doesn't appreciate the user changing the partitions on the disk after it is installed. You can attempt to boot into safe mode if you like (after selecting to boot windows, keep hitting F8 and you should get a menu that you can choose safe mode.

---

### Post by OzzyBuntu on 2008-08-04
Thanks for your answer Cyber, but it still didn't work, the Blue Screen of Death still appeared in safe mode....
This tells me a lot about windows at least.... the only reason i'm trying ubuntu is to drop windows inthe first place, even though im an avid gamer!

edit: by the way, windows no longer appears as "Boot from HD" in rEFIt menu, it appears as "Partition 4".
This only appeared after i solved a bug i had that didn't allowed me to boot Ubuntu from HD. May

---

### Post by cyberdork33 on 2008-08-04
well in that case you might need to boot from the windows cd and "repair" your install...

---

### Post by OzzyBuntu on 2008-08-05
i've reinstalled windows and it works fine, but im going to delete windows partition and reinstall it through bootcamp.
thanks for your help!

---

### Post by cyberdork33 on 2008-08-05
> **OzzyBuntu said:**
> i've reinstalled windows and it works fine, but im going to delete windows partition and reinstall it through bootcamp.
thanks for your help!
"bootcamp" won't make any difference from what you just did...

---

