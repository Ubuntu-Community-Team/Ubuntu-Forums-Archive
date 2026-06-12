---
title: "[SOLVED] How do I backup icon packages?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by mezcla on 2007-08-14
I downloaded an iconset from gnome-look and have, over the past few months, tweaked it here and there by adding new icons which were not included.  Many of these icons are links instead of actual .pngs, so I want to know how to back up an icon set to another folder without losing all of the links in the package.  I need to wipe my system and would like to retain my current iconset.

Thanks in advance for any help.

---

### Post by aysiu on 2007-08-14
Are the links to default packages or to other manually installed icon sets?

---

### Post by mezcla on 2007-08-15
The links are part of that icon set.  They are all links to other icons within the same set.  For example, I have the icon:

gnome-package.png

the following icons use the same image and are links to gnome-package.png:

gnome-mime-application-x-archive.png (pictured)
gnome-mime-application-x-compress.png (pictured)
package.png
package-new.png
package-x-generic.png

etc.

When I compress the folder or try to move it to my external HD for backup, I lose all of the links.

---

### Post by mezcla on 2007-08-15
Ok I think I resolved it.  Originally I was moving the folder to my external drive without archiving the icons, so I was losing all of the symbolic links.  Thanks for your attention regardless aysiu.  I promise I had tried to archive the folder before posting but thought the symlinks were not being preserved.

---

