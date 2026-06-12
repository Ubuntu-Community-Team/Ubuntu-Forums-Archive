---
title: "[SOLVED] Certain Applications are freezing!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-10-07
**Here is what the problem is**
Any applications that I run as gksudo load, (such as nautilus) I can see the application, I can roll my mouse over the buttons, but if I click one of the buttons, Nautilus freezes. If I press CTRL + ALT + BACKSPACE, and log back in at the GDM greeter, the screen goes black and never shows my desktop.

I just discovered last night, that Totem is freezing also.


**Here is what I have tried**
I opened another gnome-session on Virtual Terminal 8 as Root, so I am viewing everything as root, and Nautilus works, every Administrator Application works, Dangerdeep (A submarine game that will not work as a regular user) works perfect as Root. Everything practically works as root.

I have tried creating another user (since the problem began), placed him in the admin group, and everything happens the same to him, as to my account.

I have tried changing GTK Themes, but alas, the same prevails.

Nautilus works perfect as my normal user, and does not freeze. But if I run 'gksudo nautilus' or gksu or sudo, it freezes. But yet on the root session, it works prefect. I do not understand it, but I can not live the rest of my system's life as root.

I REALLY NEED HELP!!
So, if anyone could help, suggest, recommend, give advice, I WOULD APPRECIATE IT!
I am quite desperate, as I have become quite irritated over the matter, and have rebooted my system at least 12 different times trying to get this to work, but every time a failure.

PLEASE!

Dr Small

---

### Post by mike555 on 2007-10-07
Are you using an ATI graphics card?  I've had some problems with mine , so I bought an Nvidia  card , now no problems .......

---

### Post by Dr Small on 2007-10-07
I am using a nvidia card.

Here is the output of ~/.xsession-errors:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "drsmall"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/selftech-server:/tmp/.ICE-unix/5774
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
Initializing gnome-mount extension
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"

(gnome-panel:5999): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
sox: Unknown input file format for '-':  File type 'wma' is not known
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"
/home/drsmall/.themes/Fusions/gtk-2.0/gtkrc:72: Unable to locate image file in pixmap_path: "efefef"

---

### Post by Dr Small on 2007-10-07
I just tried and tested another thing.
If I run 'gksudo thunar' (the xubuntu file manager), everything works perfect in it.

So that escapes the idea of gksudo or gksu needing to be reinstalled. It keeps pointing to some GTK application, but I do not know what!

Dr Small

---

### Post by Dr Small on 2007-10-07
I have backed up all my important data, so I am preparing for a reinstall since the problem could not be solved.

Dr Small

---

### Post by askhan on 2007-10-14
I have the same problem, could this be a virus? and did your re installation fix the problem?

---

### Post by askhan on 2007-10-14
No reply? :(

---

### Post by Dr Small on 2007-10-15
> **askhan said:**
> I have the same problem, could this be a virus? and did your re installation fix the problem?
I would not say it was a virus, but more of some misoncofiguration of some file, that most likely corrupted somehow.

Yes, my problem was solved by reinstalling the operating system.

Dr Small

---

### Post by askhan on 2007-10-15
Totem works after I disabled ESD. I think that was what was causing all the problems.

---

### Post by Dr Small on 2007-10-15
What is ESD ?

---

