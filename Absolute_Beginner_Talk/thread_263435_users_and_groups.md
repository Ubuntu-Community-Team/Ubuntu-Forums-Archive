---
title: "users and groups"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by wardr1va on 2006-09-23
i am busy reading a book beginning unix by paul love.
when i try to view /etc/shadow file it says that i do not have
permission.

im sure i am an administrator although i read that administrator
accounts usually have an id of 0...i am 1000.
what group should i belong to in ubuntu to be a superuser?
the admin group or $user

:(

---

### Post by kidders on 2006-09-23
Never add yourself to the root group! Doing so would give any number of malicious programs/people carte blanche on your system!

**Edit:** To read /etc/shadow, you should log in as root ... don't play with the file's permissions. In case you're unaware, **never ever ever** log into a _graphical_ environment as root though. Sorry... forgot to actually say how to access the file!

---

### Post by bulldog on 2006-09-23
> **wardr1va said:**
> i am busy reading a book beginning unix by paul love.
when i try to view /etc/shadow file it says that i do not have
permission.

im sure i am an administrator although i read that administrator
accounts usually have an id of 0...i am 1000.
what group should i belong to in ubuntu to be a superuser?
the admin group or $user

:(

Try in your terminal,

gksudo nautilus

Which opens nautilus with rights as a root.

Before you alter anything make sure to mak a copy first!!!

To have root rights always use sudo and if you open a program with a GUI be sure to always use gksudo.

To become root for a longer period of time use  sudo -s wich make you root till you type exit.

---

### Post by steve.horsley on 2006-09-23
The administrator's username is **root**. In Ubuntu, root's account is disabled so you cannot log in as root (doing so is a great security risk). Members of group **admin** can run commands as though they were root by preceeding those commands with the word **sudo**. For instance, the command
**cat /etc/shadow** will tell you permission denied. But this command:
**sudo cat /etc/shadow** will succeed (sudo may want your password first - it's not asking for root's password).

If you want to run a GUI application with root privilege, use **gksudo** instead of **sudo,** like this:
**gksudo nautilus**

Be careful when running things as root - you have the power to trash the system. When not using root priviledge, you can only mess up the files in your home folder.

---

