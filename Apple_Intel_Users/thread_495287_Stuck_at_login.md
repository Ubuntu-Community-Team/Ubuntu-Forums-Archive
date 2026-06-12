---
title: "Stuck at login"
date: 2007-07-07
forum: Apple Intel Users
---

### Post by LieToPurify3 on 2007-07-07
I logged into Xubuntu for the first time in parallels, and tried to change my resolution to 1280x800 to fit my Macbook screen.  Now, when I start up my VM, it goes to the login screen, i type in my password, and then it flashes back to the boot screen that says:
*Activating swap...
                                     [ok]
*Checking root file system
fsck 1.39 (29-May-2006)
/dev/hda1/: clean, 95842/610432 files, 420214/1218924 blocks
                                     [ok]
*Checking file systems...
fsck 1.39 (29-May-2006)
                                     [ok]"

Then, it goes back to the login screen.  This happens over and over.  I think i can get into the failsafe and type commands.  Is there anything i can do in there to reset my resolution?  Why did this happen?

---

### Post by cyberdork33 on 2007-07-07
i would guess Xorg is crashing. you can try to edit your xorg.conf file to a lower resolution.

use CTRL+ALT+F1 to get to the console.

login there and you can edit with 
```
$ sudo nano /etc/X11/xorg.conf
```

---

