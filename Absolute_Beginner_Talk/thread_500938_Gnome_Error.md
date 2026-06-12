---
title: "Gnome Error"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by prodigy_00 on 2007-07-14
I'm getting this error whenever I boot up "An eror occurred while loading or saving configuration information for gnome panel. Some of your configuration settings may not work properly.
Type mismatch:Expected 'string got' got'int' fpr key /apps/nautilus/desktop/computer_icon_name"

Is there any way I can fix this?

---

### Post by starsky on 2007-07-14
hi there :)

ok go to your terminal and do this

$ gconf-editor

then navigate to /apps/nautilus/desktop/computer_icon_name ( that means go to apps then nautilus then desktop then computer_icon_name)
and type a string value for your computer icon for example, "My Computer".

HTH

Post back :)

---

