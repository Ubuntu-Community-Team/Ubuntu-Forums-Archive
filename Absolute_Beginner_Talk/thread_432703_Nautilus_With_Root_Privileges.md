---
title: "Nautilus With Root Privileges"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Bill Bickley on 2007-05-04
How do I run Nautilus with root privileges?

TIA from an obvious rookie...

Bill

---

### Post by darkrose on 2007-05-04
in a terminal type:
gksudo nautilus

---

### Post by aktiwers on 2007-05-04
Or install the scripts from Automatix2.. then you can do it with a right click!

---

### Post by Sef on 2007-05-04
> Or install the scripts from Automatix2.. then you can do it with a right click!

1) Automatix is a 3rd party project, not connected with Ubuntu.

2) It can work; however, it can cause you to have to reinstall your operating system.   I know of no way to know how it will do on your system before you try it out.   Try it at your own risk.  Be sure and back up everything.

---

### Post by aktiwers on 2007-05-05
Sef:
In what ways can Automatix2 cause you to have to reinstall your operating system?

Letting Automatix2 add 3 scripts in Nautilus script folder wont cause you to reinstall your OS?

---

### Post by Pobega on 2007-05-05
No, it won't. But suggesting Automatix2 to a newbie will inevitably cause them to bring in everything else from Automatix out of curiousity, and end up breaking their system. Suggesting Automatix in general is frowned upon, unless the person knows what he/she is doing.

---

### Post by STREETURCHINE on 2007-05-05
you can do 

     ```
gksudo nautilus
```

in terminal.

or install automatix (dont believe all the gibberish you here about it ,it is a very usefull tool)

---

### Post by aktiwers on 2007-05-06
> **STREETURCHINE said:**
> you can do 

     ```
gksudo nautilus
```in terminal.

or install automatix (dont believe all the gibberish you here about it ,it is a very usefull tool)


Agree

---

### Post by junjan on 2007-05-06
If you want to have it forever, you can add it as a menu entry:

Right-click on Applications, then Edit Menus. Into System Tools create a New Item:
Type: Application
Name: Root Nautilus (Or whatever you like)
Command: gksudo nautilus
Icon: Select one pixmap you like

Voila! :)

---

