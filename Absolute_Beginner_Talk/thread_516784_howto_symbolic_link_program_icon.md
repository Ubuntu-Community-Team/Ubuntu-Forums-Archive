---
title: "howto: symbolic link program icon"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-08-03
Hi:

I installed Seamonkey (f/k/a Mozilla) into /usr/local/seamonkey. I now want to create an icon on my desktop and also an entry under appications>internet so I can start Seamonkey without using the command line.

I believe I need to create symbolic links to do this - and I have created symbolic links before - e.g. for Java - but I was following Sun's how-to and I have no clue how to do it on my own.


Thanks in advance.

--GM

---

### Post by Inxsible on 2007-08-03
To create a symbolic link do ```
ln -s /path/to/real/file /path/to/non-existent/file
```

---

### Post by mgmiller on 2007-08-03
To create an entry in your Applications menu:
Right click the word Applications in the top panel and then left click "Edit Menus".  Navigate to where you want the new entry to be and create it and put in the command with full path.  It's all GUI'fied and easy.

To put an icon (launcher) on your desktop:
Right click a blank area on your desktop and left click "create launcher".  You then put in the path to the program and can specify an icon by clicking on the icon button.

Note that icons on your desktop are scalable.  Right click the icon and select "Stretch icon" and grab a corner and stretch away.

---

### Post by GMachine_24 on 2007-08-03
hey there mg:

thanks for your directions. they worked perfectly.

ok, so this is kind of embarassing.... but i read about the 'gnome main menu' where all these icons/links/whatever are located.. but... how does one access it? i have looked for it and never found it and now i'm finally tired enough that i will put  my pride aside and just ask.. 

so... someone.. PLEASE... just point me there.

thanks.

gm

---

### Post by atomkarinca on 2007-08-03
main menu is the menu that you see "applications-places-system" links on. if you have a start-menu-like menu with just the ubuntu icon on it, that's called main menu.

---

### Post by GMachine_24 on 2007-08-04
thanks. :)

---

