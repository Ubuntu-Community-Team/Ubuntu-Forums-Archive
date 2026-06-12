---
title: "Icons"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-01-21
How can I change the icons of some files such as ppt files? In dolphin file manager no icon is seen but the same thing doesn't happen in nautilus? Also how can the icons of the shortcuts be changed (Link to location)?

---

### Post by erginemr on 2008-01-21
AFAIK, you cannot change the icons of, say, all PPT files that easily. They are part of the GTK Theme you are using and are located in subfolders of /usr/share/icons as part of a complete set of icons. 

You can customize the icon set of your theme neverthless. Right-click on your desktop, select Appearance/Background, activate the Themes tab, press the Customize button and select another icon set. 

You can find more icons, themes, login screens, etc. at:
[www.gnome-look.org](www.gnome-look.org)

On the other hand, changing the icon for a shortcut, and even for a single file (say, one specific PPT file) is easy: All you need to do is to right-click on the file, and click on the button where the file's icon is shown. Common places to select a customized icon are:
```
/usr/share/icons
/usr/share/pixmaps
```

---

### Post by Arthur Archnix on 2008-01-21
Like said above, it's controlled by your theme. I was using an icon theme that I really like except for the zip archives. So I replaced that file with another that I liked better from another theme.

The icons for themes that you install can be found in ~/.icons

There's a folder in your theme folder called "mimetypes". It goes something like this:

~/.icons/your_theme/scalable/mimetypes/

If you browse that folder in nautilus you'll see the icon that you want to replace. Just rename to something like "zip.icon.backup" and replace it with the icon you want to use. The icon you want to use must have the exact same name as the one that you are replacing.

Themes that came installed with ubuntu are found in /usr/share/icons

---

