---
title: "Wheres the program I installed?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Punkristo on 2008-03-27
Im having some problems here, some times when I install a program using the serminal or add and remove etc etc it installs fine but when I go to Applications I cant find it anywhere. Right now Im trying to install 7zip or winrar and they installl but dont appear on the Applications menu. Help please!

---

### Post by markekeller on 2008-03-27
Not all programs are added to the menu.  You can add them in yourself, if you want, or run them from the terminal.  The best way to do that is to open Synaptic (the real name of the "Add and Remove" program), find the package you just installed in the list, click "Properties", and switch to the "Installed Files" tab to see what files it installed.  You ought to be able to find the filename of the program in there.  Then you can run it!

And if you want to add a program into the Applications menu, that's pretty easy to do, to.  In the menu, go to "System -> Preferences -> Main Menu", navigate to the category you want to put it in, and then click  "New Item."  It's pretty intuitive.

---

### Post by PinkFloyd102489 on 2008-03-27
7zip and Winrar arent GTK programs, they're command line programs.


Try typing "man p7zip" and "man rar" in the terminal.

---

### Post by Punkristo on 2008-03-27
So how do I add a program to the menu?

---

### Post by (((X))) on 2008-03-27
Rightclick om menu, then select edit.
Menu editing application will be opened, checkmark applications you would like to be visible.

---

### Post by wolfen69 on 2008-03-27
> **PinkFloyd102489 said:**
> 7zip and Winrar arent GTK programs, they're command line programs.


Try typing*** "man p7zip" and "man rar"*** in the terminal.

actually, all you need to type is the name of the program. ez.

if you right click the menus and select edit menus, you can add/delete menu items there too.

---

### Post by Asham on 2008-03-27
wouldn't  the following command show the location of the program?

```
whereis 7zip
```

I use "whereis" quite often since I never learn where the different applications are installed to.

---

### Post by forrestcupp on 2008-03-27
Making a menu entry for a command line app like those won't do you any good.  They have to be run from the command line.

---

