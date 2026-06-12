---
title: "Running GUI programs with root priviledges"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Zahrber on 2007-02-13
How can I run NmapFE GUI with root priviledges. In windows this is an alternate click run as on the executable or shortcut

I have looked around and haven't found it so does someone know this simple task. I am sure in the future I will need to run other programs like this also....

---

### Post by Bachstelze on 2007-02-13
Iin a terminal, *gksudo comand*. If you're running KDE, use *kdesu* instead.

---

### Post by Zahrber on 2007-02-15
Thanks but I know how to run superuser from command line that is simple. 

What I am trying to find out is how to run a program that is GUI based and is started with a link with root priviledges if anyone can tell me this please. I am still looking.

---

### Post by ardchoille42 on 2007-02-15
If you have a menu item or launcher that launches an app, and you want to have that launcher launch the app as root, change the command for the launcher from appname to gksudo appname.

---

### Post by sumguy231 on 2007-02-15
> **Zahrber said:**
> Thanks but I know how to run superuser from command line that is simple. 

What I am trying to find out is how to run a program that is GUI based and is started with a link with root priviledges if anyone can tell me this please. I am still looking.

That **is** how you start a graphical program with root privileges, with or without links. You can type it in the run dialog if you want to.

---

### Post by anubhavrocks on 2007-02-15
On the Desktop right click->Create Launcher
Once you do that in the "Command:" field put the application name.
For example if i want a root terminal, i write gksudo gnome-terminal.

---

