---
title: "I need some help installing an icon pack.."
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-18
Is there/What is   the terminal command to install this icon pack..?

**icons.tar.bz2**

This is the gentoo icon pack i found here:[http://www.gentoo.org/dyn/icons.xml]("http://www.gentoo.org/dyn/icons.xml")

[IMG]http://www.gentoo.org/images/icons/l33t_DEV_kcmdevices.png[/IMG]

---

### Post by bluefrog on 2006-08-18
if memory serves (not on ubuntu right now):

open system/preferences/themes
click on the icon tab, drag and drop your bz2 file in the tab, that should work.

James

---

### Post by kepos on 2006-08-18
System -> Preferences -> Theme

there you select Theme Details and under tab called 'Icons' it says: 'New themes can also be installed by dragging tem into the window'

just drag and drop them

---

### Post by jason.b.c on 2006-08-18
> **kepos said:**
> System -> Preferences -> Theme

there you select Theme Details and under tab called 'Icons' it says: 'New themes can also be installed by dragging tem into the window'

just drag and drop them

No it dosen't work that way , Thats why i need the terminal command...

**invaled format:**

---

### Post by Karma_Police on 2006-08-18
That isn't an icon theme. Just a collection of icons. You can put them in any folder, and then use them by changing the icon in a program launcher, but that's it.

---

### Post by jason.b.c on 2006-08-18
> **Karma_Police said:**
> That isn't an icon theme. Just a collection of icons. You can put them in any folder, and then use them by changing the icon in a program launcher, but that's it.

How do i extract them to: **/usr/share/pixmaps**...????     I don't have root permissions to that folder...

---

### Post by kepos on 2006-08-18
yeah, i downloaded now and i looks to me as just a group of icons.

you can copy them using sudo and cp command


or just type
[INDENT]sudo nautilus[/INDENT]
and copy them normally. :)

---

### Post by jason.b.c on 2006-08-18
I figured it out , I just had to show hidden files and folders....

---

