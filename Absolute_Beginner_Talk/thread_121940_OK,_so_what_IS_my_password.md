---
title: "OK, so what IS my password?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-01-26
Added some APPZ last night (after my F-Prot fiasco), specifically the ADD PRINTERS part. 
When I tried to run it (to install my CANON printer) it asked for the password to run "foomgui" (or some similar name) to which I gave my root password. Then, it asked for another password, don't know if it was expecting something new, so I gave it the same password. It then shut down and now refuses to run at all...what did I do?

---

### Post by endersshadow on 2006-01-26
You need to input your user password, not your root password.  It's running as sudo, not root.

---

### Post by qwazert on 2006-01-26
I think I tried BOTH to no avail...

I'll have to check again when I get home!

---

### Post by aysiu on 2006-01-26
Why do you have a root password?
Did you do an expert install?

---

### Post by Klaidas on 2006-01-26
Make sure you type it correctly. The passwords are case sensitive

---

### Post by qwazert on 2006-01-27
Just checked it again and yup...it's asking for ROOT password:

***"To run the program usr/bin/foomatic-gui, you need to enter the ROOT password"***

---

### Post by aysiu on 2006-01-27
You shouldn't have a root password unless you did an expert install or somehow enabled the root account. Even so, when you need root privileges, you will use your user password and the root password will not be recognized.

It sounds confusing, but there's actually a reasoning behind this. To read more, see the third link of my signature or [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by llambo on 2006-01-28
I have the same problem as qwazert. I did a basic instl and have been trying to install my printer, but I get the  To run the program usr/bin/foomatic-gui, you need to enter the ROOT password as well. I am so verry new to this that what ever you say has already gone over my head. I'm just trying ubuntu to see how it is. Thanks for any reply and suport. So far this forum is rather interesting.

---

### Post by aysiu on 2006-01-28
I'll try to simplify it for you as best I can:

There are root *privileges*, and then there is a root *account* with a root *password*.

Most Linux distributions give you one regular user with one regular password. Then, they give you one root user with one root password.

Ubuntu and Mac OS X give you one user who ordinarily operates as a regular user but who can also, with a password prompt (the *user* password) temporarily gain root *privileges* even though there isn't a root account you can log into.

The foomatic thing asks for the "root" password because most Linux distributions have a separate root *account*, and to run the setup for your printer you need root *privileges*, so your printer assumes you need a root account, since that's how most Linux distributions do it.

That's not how Ubuntu works. If you want to run a command with root privileges, you put the word *sudo* in front of the command and enter your *user* password. If you want to run a graphical command, you put the word *gksudo* (for Gnome) or *kdesu* (for KDE) in front of the command.

For example, if the command is ordinarily ```
foomatic-gui
``` you would instead use the command ```
sudo foomatic-gui
``` and enter your **user password**, which will temporarily gain you **root privileges**.

---

