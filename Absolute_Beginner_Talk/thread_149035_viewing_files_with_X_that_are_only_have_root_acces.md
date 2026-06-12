---
title: "viewing files with X that are only have root access"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-23
how can files be viewed with X if they are  root restricted

ie

places/computer/filesystem/etc/dd/asasas.txt


asasas.txt is only acessable by root.

lex1;) ;)

---

### Post by dcstar on 2006-03-23
[QUOTE=lex1]how can files be viewed with X if they are  root restricted

ie

places/computer/filesystem/etc/dd/asasas.txt


asasas.txt is only acessable by root.

lex1;) ;)[/QUOTE]
Create a Launcher with the following command:

gksudo "nautilus --browser %U"

---

### Post by Gustav on 2006-03-23
Or better yet: create a script that can open files as root.

Make a file in ~/gnome2/nautilus-scripts (you can open that folder by right-clicking, chosing "scripts" and "open scripts folder") named "open as root" (or whatever you want).

Paste this into it:
```
#!/bin/bash
#

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```
Change the permissions of the file so that you can excecute it: right-click the file, open properties click on the permissions tab and check the apropriete check boxes.

Now you can open files as root by right-clicking at them, chose scripts and "open as root".

edit: this script can open all files and even folders :)

---

