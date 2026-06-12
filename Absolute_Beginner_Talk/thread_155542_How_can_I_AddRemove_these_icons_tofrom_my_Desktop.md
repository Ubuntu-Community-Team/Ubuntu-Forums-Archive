---
title: "How can I Add/Remove these icons to/from my Desktop?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-05
Hello!!!

I would like to know how can I add/remove the following icons to/from my Desktop.

On a Restart they showed up automatically & I would like to know how they did...

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/Screenshot4.png[/IMG]

Thanks.

---

### Post by mlind on 2006-04-05
launch gconf-editor from terminal  and look /apps/nautilus/desktop.
There should be some checkboxe's for disabling those icons.

---

### Post by dvarsam on 2006-04-05
[QUOTE=mlind]launch gconf-editor from terminal  and look /apps/nautilus/desktop.
There should be some checkboxe's for disabling those icons.[/QUOTE]

I can NOT open it, the way you suggested, by typing:

# gconf-editor

I get the following:> Gtk-WARNING **: cannot open display:

Can I do it from the Desktop's Menus instead?

---

### Post by meborc on 2006-04-05
u can use smeg (gnome menu editor) to add gconf (or whatever it is called... i think it was smth with configuration) to your apps menu... then access it from there

---

### Post by Zimmer on 2006-04-05
Applications>System Tools>Configuration editor...
and look for 
/apps/nautilus/desktop.
You can also set the desktop to display the contents of your home folder on the desktop. I find this most useful.

---

### Post by dvarsam on 2006-04-05
[QUOTE=Zimmer]Applications>System Tools>Configuration editor...
and look for 
/apps/nautilus/desktop.
You can also set the desktop to display the contents of your home folder on the desktop. I find this most useful.[/QUOTE]

Thanks man!!!

This Works!!!

---

