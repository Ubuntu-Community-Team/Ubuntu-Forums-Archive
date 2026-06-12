---
title: "Easy one"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by nikolaos on 2008-01-11
This is an easy (propably silly as well) question. So here it goes:

I want to open a terminal from the gnomw windows manager so i can start working at the directory the manager was in. I am trying to avoid all those cd's.
I hope you will find this easy to answer and that you will..........................answer!!!

---

### Post by bollix47 on 2008-01-11
[http://ubuntuforums.org/showthread.php?t=661498&highlight=nautilus+terminal](http://ubuntuforums.org/showthread.php?t=661498&highlight=nautilus+terminal)

---

### Post by kernel tom on 2008-01-11
i belive a right-click should open a menu and "open terminal here" should be an option, it will open a terminal in that directory

kt

---

### Post by nikolaos on 2008-01-11
Thanks bollix47  that was really helpfull (exactly wat i needed). Thanks a a lot!

---

### Post by beercz on 2008-01-11
Here's one way:

If you want to open terminal in the /tmp directory, open terminal as normal and type:

> gnome-terminal --working-directory /tmp

You can edit the menu short cut for terminal and add --working-directory /tmp to the command.

To do this right-click on the Applications menu, and choose Edit Menus, navigate your way to Terminal (in the Accessories menu) and in the right pane, right-click Terminal and choose Properties.

Simply add  --working-directory /tmp in the Command field, so it reads:

> gnome-terminal --working-directory /tmp

Just substitute /tmp with whatever directory you wish to start in.

There are lots of other options as well.  In terminal type:

> man gnome-terminal

---

