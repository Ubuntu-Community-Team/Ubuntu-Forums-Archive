---
title: "Itunes in Wine?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by thisxcantxexist on 2008-04-11
i'm currently running itunes in wine. everything works great except i cannot set my library to my external harddrive(fat32) where i keep all of my media.  My HD shows up on the desktop and i am able to access all of my media through rhythmbox. Can anyone tell me how i can get itunes to recognize my harddrive?

---

### Post by warbread on 2008-04-12
If you haven't already, run 'gksudo winecfg', go to the 'drives' tab and hit 'autodetect'.  That may help the external show up in wine's file browser.  

If that doesn't work, the easiest solution I can think of is to mount your external to a folder in ~/.wine/drive_c , or where you want, and then point iTunes to that folder.

---

### Post by david_kt on 2008-04-12
> **warbread said:**
> If you haven't already, run 'gksudo winecfg', go to the 'drives' tab and hit 'autodetect'.  That may help the external show up in wine's file browser.  

If that doesn't work, the easiest solution I can think of is to mount your external to a folder in ~/.wine/drive_c , or where you want, and then point iTunes to that folder.

Do not run with gksudo or sudo. Just run winecfg will do.

DK

---

### Post by joshrobinson on 2008-04-12
you should be able to get out of the c: from wine, and get back into your linux filesystem, then just browse to your external drives location

---

