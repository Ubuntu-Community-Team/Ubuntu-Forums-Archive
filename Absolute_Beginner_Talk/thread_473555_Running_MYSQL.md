---
title: "Running MYSQL"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-06-14
I have just successfully installed MySQL. I can see the binaries but it does not appear in my menus. Any idea how to crank it up?

Thanks.

---

### Post by KIAaze on 2007-06-14
I think MySQL is a command-line based app, no?
(launched by typing "mysql" if I remember correctly.)

Anyway, here's a post I wrote recently on how to create shortcuts:
======================================================

That's because shortcuts are not always installed by default.
It's up to those who create the binary packages to add launchers to be installed automatically.
If they don't, you can still easily do it yourself. It's not done the same way as in Windows (which I find more intuitive), but it's not hard either.

How to create a shortcut manually:
First of all, find out the command used to launch the program.

_GUI method:_
Right-click on the menu bar and select "edit menus". (Or open a terminal and type "alacarte")
It will launch a GUI to add menu entries.

Go to the section where you want to add the shortcut in Alacarte and push the "New Item" button. Fill in;

-Name: whatever you want
-Comment: whatever you want
-Command: command used to lauch the program from a terminal
-Icon: whatever you want

_CLI method:_
(here with an example shortcut for the Loose Cannon game (copied from the Ubuntu Gamers Arena site))
```
sudo nano /usr/share/applications/Loosecannon.desktop

```

Add the following;

> [Desktop Entry]
Name=Loose cannon
Comment=3rd person action adventure game.
Exec=loosecannon
Icon=/usr/local/share/loosecannon/pics/smg.png
Terminal=false
Type=Application
Categories=Application;Game;

Save and exit: ctrl+o, ctrl+x

You can find other examples by opening existing .desktop files in "/usr/share/applications".

---

### Post by linuxforrealpeople on 2007-06-14
Many Thanks

---

### Post by linuxforrealpeople on 2007-06-14
I a having problems starting at the command prompt and am getting a permissions error "Access denied for user 'dwaine'@'localhost' (using password: NO)"
?
Thanks

---

### Post by hyper_ch on 2007-06-15
Well, mysql has it's own authorization.... after install you have only a root user in mysql with now password set...

---

### Post by az on 2007-06-15
Mysql server is started up when you install it and it also starts up at boot time. 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

