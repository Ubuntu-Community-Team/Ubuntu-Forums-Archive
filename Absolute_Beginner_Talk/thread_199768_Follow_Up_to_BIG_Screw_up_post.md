---
title: "Follow Up to BIG Screw up post"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-06-19
Okay i am trying to fix the master boot record, since my comp doesn't boot to windows since the GRUB boot is messed up from a Ubuntu/XP dual boot.

Good folk on this forum have directed me as to how do this, however, my parents 'installed' XP on this and they don't know/remember the adminstraor password which the system wants in the Repair option. 

My account on windows has adminstraor priviliges but i have no password, but if i put no password at the prompt it rejects it...

i relaise it's not Ubuntu stricyly...but HELP ME!!!!

---

### Post by anaconda on 2006-06-19
Well..
You dont really need the password!
Just get any dos/win95/98 boot disk (or CD) and after booting type:

fdisk /mbr

it restores the MasterBootRecord so that windows boots again.  Really... Microsoft hasn't changed how mbr works since MSDOS 5.0 So it doesn't matter which version you use. And the older ones don't ask passwords..

One other thing you may want to do (if this alone doesnt work) is  to type fdisk, and from there mark the windows partition active...  (it probably already is..)

For windows to boot mbr must be acceptable, and windows partition must be active..

This is the same that XP:s fixmbr (or was it fixboot) does..

Or then you coud install ubuntu or about any linux again, and install grub, and boot windows from there...

If all else fails, then you can always boot with knoppix (or ubuntu) liveCD, and rescue all the data you want to rescue, and then reinstall XP...

---

### Post by anaconda on 2006-06-19
Oh and if you dont have dos boot floppy, you can try freedos, or copy it from somewhere..

google "fdisk /mbr" for more info..

---

