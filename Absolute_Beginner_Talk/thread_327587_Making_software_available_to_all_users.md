---
title: "Making software available to all users"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by charlieo on 2006-12-29
Just installed Dapper on toshiba laptop.  I have loaded some new software (gnucash).  I can not add gnucash to menu.  The executable is in /usr/bin directory,but owner is root.  I know I am missing something simple.  How do I make gnuchas available to all users as well as other programs that I install.  Thanks in advance.
charlieo

---

### Post by Arisna on 2006-12-29
The owner is root, but all users should already have read and execute privileges to the executable.  You can add GNUCash to the menu using the Alacarte menu editor.  Point the entry to /usr/bin/gnucash and you should be good to go.

---

### Post by steve.horsley on 2006-12-29
The fact that root owns the executable is not the problem (root owns pretty-much all the executables you are currently using). The problem is that you don't know how to add gnucash to the menu. 

For a single user:
Right-click the Ubuntu icon and choose Edit Menus. 
Navigate the tree to where you want to where you want the new entry to be and click New Item. As Arsna says, you need to launch /usr/bin/cnucash.

To make a single change and make the application appear in everybody's menu is harder. There are files in /usr/share/applications that do this and you could try and copy what's there, but it's not the full story. I don't yet understand how the Categories section in these files relate to the menu submenus.

---

