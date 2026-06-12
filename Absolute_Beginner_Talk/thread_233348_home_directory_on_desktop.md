---
title: "home directory on desktop"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by juicymixx on 2006-08-10
Hello,
 
   On the desktop my new(ish) install of Dapper is an icon for my drive containing my windows partition (hda1).   It's been there since I got Dapper up and running.   Ideally I'd want an icon for my home directory INSTEAD of one for hda1.   Is there some checkbox that needs setting to get this?

Thanks.

---

### Post by skale on 2006-08-10
ln -sv ./ ./Desktop/My\ Home\ Directory
Makes a symbolic link (read: shortcut) to the home directory on the desktop.

Ain't no checkboxes here. You'll dislike them soon, give it a week or two.

---

### Post by aysiu on 2006-08-10
Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes_Visible ```
ln -s /home/juicymixx /home/juicymixx/Desktop/juicymixx
```

---

### Post by mcduck on 2006-08-10
> **aysiu said:**
> Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes_Visible ```
ln -s /home/juicymixx /home/juicymixx/Desktop/juicymixx
```
You know, there's also option to show home icon on desktop in gconf-editor.. Actually in the very same place where the option to show mounted drives on desktop is :)

It's apps/nautilus/desktop/show_home_icon (if I remeber right) :

(Symlinks work too, but you won't get correct icon for it, and you can remove the symlink by accident whereas this icon won't go anywhere unless you disable it again from gconf-editor)

---

### Post by juicymixx on 2006-08-13
thanks mcduck, and everyone else...   home_icon_visible was exactly what I was looking for!;)

---

