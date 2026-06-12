---
title: "howto add seamonkey 1.1 to the gnome applications list"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-01-23
I have downloaded the seamonkey 1.1...tar.gz
and extracted it by tar -zxvf **.gz,
running the ./seamonkey-installer command

but I can only run seamonkey from the shell command line, it is '/usr/local/seamonkey/seamonkey &' every time, it's boring, so I make a soft link,
first cd to /usr/local/bin   and
ln -s /usr/local/seamonkey/seamonkey ./seamonkey
but this still need to run it from command line,

well, how to add it to the 'applications' list? I'm running ubuntu 6.10, gnome now.

---

### Post by geokok1981 on 2007-01-23
You can add apllications easily through the alacarte menu editor. Go to:
System-->Preferences-->Menu editor (or similar name, my menu is in greek you see).
From there select the sub-category in which u wish to add the new app (lets say internet for seamonkey) and select "add new object".
A dialog pops up that allow u to add a name for the app, the command to launch it (should be the same as the one u provide in the terminal) and an icon if u wish.

---

### Post by matiz on 2007-01-23
On my desktop, System-->Preferences contains 2 entries:
System-->Preferences-->Menu Layout
System-->Preferences-->Menus & Toolbars

but no menu editor, have tried Menu Layout and failed, do I missed some packages?

---

### Post by konst88 on 2007-01-23
What do you mean by failed? The menu layout has an option to add an item to the selected menu.

---

### Post by geokok1981 on 2007-01-23
> **matiz said:**
> On my desktop, System-->Preferences contains 2 entries:
System-->Preferences-->Menu Layout
System-->Preferences-->Menus & Toolbars

but no menu editor, have tried Menu Layout and failed, do I missed some packages?

Menu Layout is what you need, my mistake.
PLease describe failed more specifically if you can. It is really straightforward, I am sure we can make this happen :)

---

### Post by matiz on 2007-01-23
:lolflag: 
Oh~~ Wowoooo ~
After restart my linux box, I found the seamonkey icon is appeared on the program list !

---

### Post by emarkay on 2007-01-28
I clicked on the little Ubuntu logo on the upper left corner and the "Alacarte Menu Editor" appeared.  That is how I added SM to the menu list.

---

### Post by vincentvee on 2007-02-27
> **emarkay said:**
> I clicked on the little Ubuntu logo on the upper left corner and the "Alacarte Menu Editor" appeared. That is how I added SM to the menu list.
giving up in frustration........i can't even get it to run with a command

---

