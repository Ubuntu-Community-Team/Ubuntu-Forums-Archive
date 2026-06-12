---
title: "Cant Delete Item from Trash"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-06-06
When I try to Open yahtzee from the trash I get this  "/home/name..rapper.Po" cannot be deleted because you do not have permissions to modify its parent folder.


I looked for The rapper.po but cant find it

---

### Post by kernel tom on 2007-06-06
restore it

then use this command to delete it permantly from the terminal

sudo rm -rf /path/to/folder/foldername

---

### Post by benanzo on 2007-06-06
[COLOR="DarkRed"]**EDIT:**[/COLOR]
[COLOR="DarkRed"]Are you wanting to restore items from the Trash or remove them from the Trash?
These instructions are for cleaning out the Trash of everything:
[/COLOR]
Sometimes items end up in the trash that you (as your normal user) can't delete.

To empty the trash of all its contents no matter who owns the files in it do:

Open a terminal **Applications -> Accessories -> Terminal**
and move to the .Trash folder:
```
cd ${HOME}/.Trash
```
permanently remove everything inside:
```
sudo rm -rf *
```
You should need to enter the root password

Then close the terminal.

You should immediately see your Trash icon empty.

---

