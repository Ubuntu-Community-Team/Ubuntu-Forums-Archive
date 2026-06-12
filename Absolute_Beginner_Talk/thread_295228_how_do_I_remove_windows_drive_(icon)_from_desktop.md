---
title: "how do I remove windows drive (icon) from desktop?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Angry on 2006-11-07
How do you remove the windows drive icon from the desktop?  Right-clicking the icon only shows a disabled "Move to Trash" entry (but the Unmount volume is enabled - but I don't want to do that anyways).

I had set up read/write access to my windows drive (using ntfs-3g) on boot and mapped it to /media/windows.

As far as anything else is concerned, everything is fine, it shows up in my "Places" menu and as an icon in nautilus at the "Computer" level.

Thanks in advance.

---

### Post by 23meg on 2006-11-07
Launch gconf-editor and change the /apps/nautilus/desktop/volumes_visible key to false.

---

### Post by dbott67 on 2006-11-07
From the terminal, type:
```
gconf-editor
```
And uncheck **/apps/nautilus/desktop/volumes_visible**

-Dave

---

### Post by Angry on 2006-11-07
Holy crap - quick response!
And thanks.

I think this is the second time I've needed that gconf-editor in as many days.  Prior that, never even heard of it (not that I've been a long time user of Linux) - it seems like it should be a more visible component (ie. shown from the Application menu or similiar) of the gnome desktop.

---

### Post by dbott67 on 2006-11-07
Right-click on the Applications menu & select 'Edit Menus'.

From there, select the APPLICATIONS menu > SYSTEM TOOLS and place a check in CONFIGURATION EDITOR.

-Dave

---

