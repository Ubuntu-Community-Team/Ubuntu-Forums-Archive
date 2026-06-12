---
title: "where do apps go after i install them?"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by yellowband on 2005-08-14
Hey everybody,

sorry for this noob question but, where are the programs installed that i choose from synaptic?

for example, i installed billiards-gl and 3dchess (games) but i can'tfigure out how to run them. where are they installed?

---

### Post by nad on 2005-08-14
If the installers behaved nicely, you can log out and back in. Then the launchers should appear in your menus.

If not... Use the command whereis app_name to find the location of the binary. Then use the "Run Application" applet to launch your program.

There is a menu editor project listed on the forum homepage that you may wish to peruse if the apps were not added to your menus.

---

### Post by aysiu on 2005-08-14
[http://ubuntuguide.org/#refreshgnomepanel](http://ubuntuguide.org/#refreshgnomepanel)
[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by invalid on 2005-08-14
some things just never make it to menues, for whatever reason.

you can always run them from a terminal, though..

try opening one, and typing the name of the game - if this does not work, you can try searching part of the name and see if it is named something different.

Cheers,
Cb

---

### Post by phen on 2005-08-14
hello!
usually, the BINary files of applications that you install are located in /usr/bin. other files are spread over the /usr/* directories. all files in /usr/bin are executable from everywhere. so you can just open a terminal and type for example:  "billard-gl" and it should start. If this is not working try to type bil<TAB> By pressing the TAB key, you activate autocomplete. press it twice (fast) to get a list off all applications starting with bil* 

The applications you install via synaptic have to have a *.dekstop file with them, when they shall add a menu entry. packages which don'T have that file dont add menu items. 

after you found out how to start the application, you can install the SMEG menu editor and add a launcher manually!

good luck :)

cheers,
kai

---

