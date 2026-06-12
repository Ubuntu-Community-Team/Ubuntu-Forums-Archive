---
title: "Folder Customization"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2008-01-02
Happy New Year to Everyone,
My first question of the new year is how can I customize my bookmark folders to make them easier to find?
Thanks,
Cygnis1

---

### Post by ARhere on 2008-01-02
you can change how a folder looks by right-clicking the icon, then left-click the picture of the icon in the "Properties" tab.

You can also add emblems to any icon you wish, but that has a bug making them too small to see.  A way to fix the tiny emblems is to 
```
sudo gedit /usr/share/icons/Human/index.theme
```
and find
[color=blue]
[scalable/emblems]
Size=128
Context=Emblems
Type=Scalable
MinSize=32
MaxSize=256
[/color]
then change Size=128 to Size=24

-AR

---

### Post by NilsE on 2008-01-02
> **cygnis1 said:**
> Happy New Year to Everyone,
My first question of the new year is how can I customize my bookmark folders to make them easier to find?
Thanks,
Cygnis1
If you are asking in Firefox it is under Bookmarks > Organize Bookmarks

If it is in Nautilus you just get to the folder you want to bookmark then click on Bookmarks at the top and click on add bookmark.  It will then show on the left of the Nautilus window. This is assuming you selected side pane under > view

You can also rename them (right click on bookmark) and move them up and down (by dragging it up or down).

---

### Post by cygnis1 on 2008-01-03
I tried both of these suggestions and they did not work.

---

### Post by ~LoKe on 2008-01-03
> **cygnis1 said:**
> I tried both of these suggestions and they did not work.

What do you mean by making them easier to find?  Adding it as a nautilus bookmark will make it show up in the leftmost panel of Nautilus.  Are you using Gnome?

---

### Post by cygnis1 on 2008-01-03
Yes I am using Gnome.  It is a Firefox folder.  I have downloaded Favicon Picker and it will change the icon of the individual bookmarks, but not the folder holding the individual bookmarks.

---

### Post by NilsE on 2008-01-03
As far as I can tell there is no way to make a different folder icon for each folder in the bookmark drop down.

---

### Post by cygnis1 on 2008-01-03
Thank you all. I have come to the same conclusion.
Cygnis1

---

