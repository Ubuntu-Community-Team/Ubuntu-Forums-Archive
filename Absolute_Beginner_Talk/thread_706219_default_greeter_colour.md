---
title: "default greeter colour"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ceecld on 2008-02-24
Hi, im looking to change the greeter colour from the default 'humna' colour. The guide im using shows a GTK+ greeter tab in the login window setup, however i dont have this in my version of Gutsy.

Any ideas?

cheers

---

### Post by bwhite82 on 2008-02-24
By greeter, do you mean GDM -- the login screen? If so, goto the CLI and open:

> gnome-control-center

You should see a 'login window' option.

If by greeter, you mean splash screen goto:

System>Preferences>Splash Screen

It should be in the control center also.

-Cheers

---

### Post by (((X))) on 2008-02-24
You probably mean that brown color shows up everytime you login to gnome.
I managed to change that by editing /etc/gdm/PreSession/Default

Locate  BackColor#DAB082
and change it to to for example: #6EE482(sort of green-metalic)
If you know HTML, that shouldn´t be a problem to choose color

---

