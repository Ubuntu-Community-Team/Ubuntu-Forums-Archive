---
title: "installing a new theme"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by pat23_2007 on 2007-08-18
Hi im trying to install a new theme from Gnome-Look but its different than the others i have installed and the readme files says to put all the files in each location. IE 

[COLOR="DarkRed"]Icons:
copy the path glass-icons to /usr/share/icons

GTK2 and Metacity(Controls and Window Decorators):
copy the patch LiNsta2 to /usr/share/themes

XMMS skin:
put the Almon-dark-blue.wsz in /usr/share/xmms/skins
[/COLOR]

But when i go to those folders it won't let me copy and paste any help with this?

---

### Post by Steveway on 2007-08-18
gksu nautilus
But be carefull, you can bork your system up if you delete something that is not in your /home directory.

---

### Post by Kosimo on 2007-08-18
you don't have the permissions to write on that folders (for security reasons)
try to use (sudo) from the terminal.

But if you really want to do it by GUI, I'm going to say some very dangerous (but useful) way:

go to the terminal and type:  >  sudo nautilus then the password:
What you're doing with this is open a super user nautilus session, witch have all permissions to write and delete everything.   BE REALLY CAREFUL ABOUT ANY CHANGE YOU DO IN THIS MODE.

---

### Post by Gremlinzzz on 2007-08-18
gksudo nautilus will give you the permission you need makes you root

---

### Post by Zalbor on 2007-08-18
Use
```
gksudo nautilus
```
instead of sudo. Don't use sudo for graphical applications.

---

### Post by Steveway on 2007-08-18
Don't use "sudo nautilus"!
You only use sudo for command-line-applications.
For graphical applications you need to use gksu.
(gksudo is just a symlink to gksu so the preffered way is gksu.)

---

### Post by Zalbor on 2007-08-18
Ha, 3 people said the same thing (almost) at the same time.
> **Steveway said:**
> (gksudo is just a symlink to gksu so the preffered way is gksu.)
Is it? I thought gksu was like su, i.e. asking you for root's password instead of your own.

---

### Post by Steveway on 2007-08-18
No, look into the directory the program is in.
You can clearly see that gksudo is a symlink that points to gksu.

---

### Post by Kosimo on 2007-08-18
> **Steveway said:**
> Don't use "sudo nautilus"!
You only use sudo for command-line-applications.
For graphical applications you need to use gksu.
(gksudo is just a symlink to gksu so the preffered way is gksu.)

Yes, but...
sudo nautilus works as well, and in my opinion have some positive point here:
If you close the terminal it closes the window as well. It can't be let open by mistake.
Is not a good idea to have a superuser nautilus open for a long.
Anyway both works ;)

---

### Post by Zalbor on 2007-08-18
You're right, I did check. It was just a misunderstanding based on the names of the commands. :)

---

### Post by pat23_2007 on 2007-08-18
ok thanks guys/gals that worked like a charm, and i was very careful  not to muck anything up.

---

