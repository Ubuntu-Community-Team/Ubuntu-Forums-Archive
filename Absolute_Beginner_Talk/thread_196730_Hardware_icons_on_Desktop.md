---
title: "Hardware icons on Desktop"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Burke on 2006-06-14
Hey, I have a feeling this is a really easy solution, but I can't figure it out.

How do I get Gnome to NOT show the icons on my desktop for removable storage (memory cards, Thumb drives, Optical discs)?

---

### Post by bruce89 on 2006-06-14
Alt+F2
```
gconf-editor
```
apps>nautilus>desktop, uncheck volumes_visible.

---

### Post by deadgobby on 2006-06-14
[http://easylinux.info/wiki/Ubuntu#How_to_show_Desktop_Icons_.28Computer.2C_Home.2C_Trash.29](http://easylinux.info/wiki/Ubuntu#How_to_show_Desktop_Icons_.28Computer.2C_Home.2C_Trash.29)

---

### Post by Burke on 2006-06-14
Awesome. Thanks very much.

---

### Post by bruce89 on 2006-06-14
[QUOTE=deadgobby][http://easylinux.info/wiki/Ubuntu#How_to_show_Desktop_Icons_.28Computer.2C_Home.2C_Trash.29](http://easylinux.info/wiki/Ubuntu#How_to_show_Desktop_Icons_.28Computer.2C_Home.2C_Trash.29)[/QUOTE]
Note this doesn't apply for Dapper.

---

### Post by H.E. Pennypacker on 2006-07-04
[QUOTE=bruce89]Note this doesn't apply for Dapper.[/QUOTE]

It does apply to Dapper Drake.  I am using Dapper Drake right now, and deadgobby's instructions worked perfectly fine for me. 

Before these instructions, I had no idea how I could have removed those annoying icons.  I was also able to add Computer (which I renamed "My Computer"), Home folder icon, and trash.  Best of all, no typing was needing.  I just needed to check off boxes.  Nice!  

It would have been better, however, if there was a more GUI way of doing this.  For example, I could right-click the desktop, and I would be able to check of boxes in some window, rather than going through the configuration editor.  I had been hoping for something like this:

[http://www.microsoft.com/mspress/books/sampchap/5398/0735614296-02.gif](http://www.microsoft.com/mspress/books/sampchap/5398/0735614296-02.gif)

A newbie shouldn't have to mess with Configuration Editor (which resembles, in some ways, the registry in Windows) to have a few icons show or disappear.

---

### Post by someusernoob on 2006-07-04
Yes, what you are showing is the best thing ever. Its not even possible to delete the Recycle Bin from the desktop or even rename it...

(yes i know it is possible when you mess in the register blabla, but not with that GUI thing)

---

