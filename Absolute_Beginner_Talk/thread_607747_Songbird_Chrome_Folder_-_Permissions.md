---
title: "Songbird Chrome Folder - Permissions"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by og.man on 2007-11-09
I need to edit a file in /usr/share/Songbird/chrome/

Every time I try to do this, I am told that I don't have permission. The folder says it is owned by root. I've tried sudo and I've tried extracting to the desktop and editing there. It's still locked. Finally, I extracted songbird.jar, edited, and created a new archive, but I still can't get the .jar file into the chrome file because I don't have permission.

I know that logging in as root is a sin worse than death and ways to do it are being systematically removed, but how else am I supposed to edit this file?

Thanks.

---

### Post by og.man on 2007-11-09
Problem solved: used gksudo nautilus.

---

