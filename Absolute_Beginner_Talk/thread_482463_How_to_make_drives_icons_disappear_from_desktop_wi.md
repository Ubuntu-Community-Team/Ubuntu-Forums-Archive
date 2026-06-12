---
title: "How to make drives icons disappear from desktop without unmounting them?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by tico on 2007-06-23
That's my question: I'd like to have my ntfs and fat partitions automounted every time I log in, but I wouldn't like to have the correspondent icons in my desktop. How to make them disappear without unmounting the drives/partitions?

Thanks.

---

### Post by kyphi on 2007-06-23
There are a number of ways to make those desktop icons disappear, unfortunately they will also make any reference in Places disappear.

The simplest but effective method is to sweep them under the carpet, so to speak.  Activate your 'show hide' buttons for the bottom panel (right click on bottom panel and go to properties) then hide the bottom panel and drag the offending icon as far down as it will go.  Then restore your bottom panel.

Not very elegant but it achieves the desired result.

---

### Post by isaacj87 on 2007-06-23
Ah...very simple! Just go to Applications->System Tools->Gconf Editor (or Configuration Editor) and open it up.

Within Config Editor goto apps->nautilus->desktop and at the bottom where it says volumes visible: uncheck it. voila!

If you don't have the config editor in system tools do this:

System->Preferences->Main Menu

Then in the left panel goto system tools and check the configuration editor.

Hope this helps!

---

### Post by kyphi on 2007-06-23
If you do as suggested by isaacj87 via the configuration editor, you will not be able to see any icons for mounted volumes on your desktop and therefore will not be able to unmount them.

---

### Post by jfinkels on 2007-06-23
> **kyphi said:**
> If you do as suggested by isaacj87 via the configuration editor, you will not be able to see any icons for mounted volumes on your desktop and therefore will not be able to unmount them.

You will certainly be able to unmount them! You just won't be able to unmount them by right-clicking their icons on the desktop!

Just type in the terminal:```
sudo umount /path/to/mountpoint
```Usually it's something like this:```
sudo umount /media/usbdisk
```

Or you could just browse to them using nautilus (the file manager) and right click on them and choose unmount from there.

---

### Post by tico on 2007-06-23
> **isaacj87 said:**
> Ah...very simple! Just go to Applications->System Tools->Gconf Editor (or Configuration Editor) and open it up.

Within Config Editor goto apps->nautilus->desktop and at the bottom where it says volumes visible: uncheck it. voila!

If you don't have the config editor in system tools do this:

System->Preferences->Main Menu

Then in the left panel goto system tools and check the configuration editor.

Hope this helps!

This is what I was looking for. Many thanks.

---

