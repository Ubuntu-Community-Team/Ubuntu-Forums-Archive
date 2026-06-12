---
title: "Installing new programs"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by caycete on 2007-03-08
I recently installed qtorrent with the Synaptic Package Manager.  However I cannot find it in my applications menus.  Any suggestions on where to find it?

---

### Post by Leonivek on 2007-03-08
Try to find where it was installed with this command:

```
locate qtorrent
```

Then you can use that location to create a menu entry.

---

### Post by dexter on 2007-03-08
I haven't installed qtorrent, so I can't try it out. Can you start it in the terminal ? Try typing qtorrent, what happens ?

---

### Post by tbodine on 2007-03-08
Hopefully it will be merely deselected in the Internet submenu.
Try right-clicking your menu and select Edit Menu, then look at all of the Sub Menus(try Internet and Accessories first) and if it's in there, make sure that it is checked so it will show up in your menu.
Otherwise try a
```
type qtorrent
```
or a
```
which qtorrent
```

and it should tell you where it is located, if it did in fact install. Then you can use where it is located to add an entry to your menu (as described earlier).

---

