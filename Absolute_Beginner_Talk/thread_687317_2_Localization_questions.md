---
title: "2 Localization questions"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by mesh_ok on 2008-02-04
Dear All,

I have Russian ubuntu with all the language packages istalled. Russian interface, etc.

1. When inserting CDROM with Russian filenames they appear as "???????" instead of Cyrillic. When mounting manually with 'utf8' option - works fine. How can this be configured to do automatically?

2. Is it possible to have English interface (gnome, firefox etc) but with default LANG=ru_RU.utf8 environment for new running applications? I don't like the way OS is localized and would prefer to use it in English, but I always have to run my favorite apps from console/shortcut with "LANG=ru_RU etc" in order to use Russian.

---

### Post by mikewhatever on 2008-02-04
> **mesh_ok said:**
> Dear All,

I have Russian ubuntu with all the language packages istalled. Russian interface, etc.

1. When inserting CDROM with Russian filenames they appear as "???????" instead of Cyrillic. When mounting manually with 'utf8' option - works fine. How can this be configured to do automatically?[quote]

You need to add that to the line for CD-ROM in /etc/fstab. Here's mine, for example:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,**iocharset=utf8**,exec 0       0


[quote]2. Is it possible to have English interface (gnome, firefox etc) but with default LANG=ru_RU.utf8 environment for new running applications? I don't like the way OS is localized and would prefer to use it in English, but I always have to run my favorite apps from console/shortcut with "LANG=ru_RU etc" in order to use Russian.

You could try editing commands invoked by programs launchers in the menu. For example, clicking on Document Vewier invokes <evince %U>, so you could add language parameters to that. Check it out in System>Preferences>Main Menu.

---

### Post by mesh_ok on 2008-02-05
**mikewhatever**,  thank you for your help

---

