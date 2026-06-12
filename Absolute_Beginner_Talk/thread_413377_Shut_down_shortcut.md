---
title: "Shut down shortcut"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by La Hechizera on 2007-04-19
Hi there,

I cannot find out how to create a shut down shortcut on the desktop which would immediately shut down the computer. Maybe you know how to do this? Please help me :(

---

### Post by wieman01 on 2007-04-19
Power button... ;-)

---

### Post by La Hechizera on 2007-04-19
> **wieman01 said:**
> Power button... ;-)

that's not exactly what I need :) I  need a shortcut

---

### Post by Danilo Leon on 2007-04-19
> **La Hechizera said:**
> Hi there,

I cannot find out how to create a shut down shortcut on the desktop which would immediately shut down the computer. Maybe you know how to do this? Please help me :(

when i installed my dapper, i had a shut down button on the upper right of the screen, is it any different from your installation?

---

### Post by La Hechizera on 2007-04-19
> **Danilo Leon said:**
> when i installed my dapper, i had a shut down button on the upper right of the screen, is it any different from your installation?

I have this red button on the panel, when I click it I have a choice to shut down log out etc., but I'd like to have something like "shut down the computer" on my desktop which would do only one function - shut down... in this case I don't want to have a choice

---

### Post by La Hechizera on 2007-04-19
:neutral:

---

### Post by sisco311 on 2007-04-19
create a luncher on the desktop

in terminal:
```
gedit ~/Desktop/shutdown.desktop
```
copy and paste this:
> [Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name[C]=shutdown
Exec=sudo shutdown -P now
Comment[C]=shutdown
Name=shutdown
Comment=shutdown


save the file and exit (Ctrl+s Alt+F4)

in terminal:
```
sudo visudo
```
add this line at the end of the file:
> **your_user_name** ALL=NOPASSWD:/sbin/shutdown -P now


where **your_user_name** is your username
save and exit (Ctrl+o Enter Ctrl+x)

to shutdown double click on the shutdown icon on de desktop

---

### Post by wieman01 on 2007-04-19
> **sisco311 said:**
> create a luncher on the desktop

in terminal:
```
gedit ~/Desktop/shutdown.desktop
```
copy and paste this:


save the file and exit (Ctrl+s Alt+F4)

in terminal:
```
sudo visudo
```
add this line at the end of the file:


where **your_user_name** is your username
save and exit (Ctrl+o Enter Ctrl+x)

to shutdown double click on the shutdown icon on de desktop
This is excellent. Thank you, Sisco!

---

### Post by La Hechizera on 2007-04-19
> **sisco311 said:**
> create a luncher on the desktop

in terminal:
```
gedit ~/Desktop/shutdown.desktop
```
copy and paste this:


save the file and exit (Ctrl+s Alt+F4)

in terminal:
```
sudo visudo
```
add this line at the end of the file:


where **your_user_name** is your username
save and exit (Ctrl+o Enter Ctrl+x)

to shutdown double click on the shutdown icon on de desktop

thanks a lot! :) :) :)

---

### Post by DFLiddle on 2008-07-01
Here's a line to add that points to the logout icon:

Icon=/etc/share/icons/Human/scalable/apps/gnome-logout.svg

So far as Visudo goes, it wasn't easy to figure out how to use the utility -- even after reading the man page. It's a real pain to navigate and edit the sudoers file with Visudo, though I understand the rationale. However, this site was helpful to me:

[http://maeks84.wordpress.com/2008/05/29/how-to-use-visudo/]("http://maeks84.wordpress.com/2008/05/29/how-to-use-visudo/")

---

