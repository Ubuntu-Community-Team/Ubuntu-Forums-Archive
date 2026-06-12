---
title: "Permissions?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Gadren on 2005-10-06
I was trying to install some alternate GAIM icons I had found on gnome-look.org, by moving the files in the tar.bz file into /usr/share/pixmaps/.  However, when I tried to do so, I was told that I didn't have sufficient permission to do so.  Using **sudo -s** in the Terminal didn't change it, and I couldn't change the read/write permissions on the pixmaps folder itself (because it said that the owner was root)...

How can I extract things like this?

---

### Post by aysiu on 2005-10-06
Open up a **Run..** dialogue from the Gnome foot menu and type in ```
gksudo nautilus
``` You'll be prompted for your password. Then navigate to /usr/share/pixmaps and cut and paste the folder there--you'll have permission.

---

### Post by Gadren on 2005-10-07
I ran that, but there's no change...I can cut the extracted files, but I can't paste them into the pixmaps directory.

---

