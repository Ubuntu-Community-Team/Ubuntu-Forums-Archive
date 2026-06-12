---
title: "Opening data with root privileges"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-08
Hello,

How can one open files root privileges? I mean not only to read, but also to edit and save files. How does this work?

---

### Post by mikeyphi on 2007-04-08
> **O-pos said:**
> Hello,

How can one open files root privileges? I mean not only to read, but also to edit and save files. How does this work?

Not sure of the question? Is this any help - [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions)

---

### Post by smurf killer on 2007-04-08
you have to use the console. when you use sudo you will get asked to enter your password, that will give you root permissions. if you want a graphical interface you could use the command gksudo gedit [path or name of the file], its as easy as that ;)

---

### Post by aysiu on 2007-04-08
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2007-04-08
> **mikeyphi said:**
> Not sure of the question? Is this any help - [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions)
Please don't use that tutorial for editing system files.

System files have their permissions and ownership for a reason, and those should not be changed. Changing system files' ownership or permissions is a quick way to screw up your system.

---

### Post by lpmurder on 2007-04-08
[COLOR="Red"]sudo -s [/COLOR]

using the terminal it to edit, remove, rename, etc.

---

