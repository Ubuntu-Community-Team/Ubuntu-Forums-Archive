---
title: "Opera refuses to lanch"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-26
Upon trying to launch Opera (9.25, trying to upgrade to 9.26 since I uninstalled 9.5 )I am presented with this error: ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported

What does this mean and why is it a chore to start Opera?  Any ideas?

---

### Post by pedro_orange on 2008-03-26
Those files you are mentioning look like Java -Runtime Env files.

Do you have the JRE installed? If not, do that.

You may also need to point Opera to the JRE via Preferences.

---

### Post by gandaran on 2008-03-26
if you installed a different opera version you'll have to delete the old home/user/.opera folder!

---

### Post by sports fan Matt on 2008-03-26
Im installing the JRE 6 runtime files and will see if that solves it...

---

### Post by sports fan Matt on 2008-03-26
When I had the JRE 6 Installed, it maade no difference..It did pop up and I saw it complaining that in the opera folder the lock file was present so I deleted it but upon restarting the same message appeared..its really odd

---

### Post by zvacet on 2008-03-26
> if you installed a different opera version you'll have to delete the old home/user/.opera folder!

Not before you export your bookmarks and mail addesses somewhere (Desktop is good place).Opera 9.5 is different then previous versions and that may be reason why you can not start version 9.25.In short,when your  bookmarks and mail addesses are safe delete all Opera files and directories.Like it never been on your comp.After that install Opera 9.26.If all this doesn´t work go to the Opera forums.They have subforum for linux.I suggest this because I belive you will find answer faster there then here,but I can be wrong too.

---

### Post by Cappy on 2008-03-26
> **zvacet said:**
> Not before you export your bookmarks and mail addesses somewhere (Desktop is good place).Opera 9.5 is different then previous versions and that may be reason why you can not start version 9.25.In short,when your  bookmarks and mail addesses are safe delete all Opera files and directories.Like it never been on your comp.After that install Opera 9.26.If all this doesn´t work go to the Opera forums.They have subforum for linux.I suggest this because I belive you will find answer faster there then here,but I can be wrong too.

I just downgraded my own Opera from 9.5 Beta to 9.25 or whatever recently.
Moving all the folders in ~/.opera (except sessions) to a new folder I made called  ~/.opera/backup
worked great for me. This won't affect bookmarks/speeddial/sessions.

If it still doesn't work you can move the folders back.

---

