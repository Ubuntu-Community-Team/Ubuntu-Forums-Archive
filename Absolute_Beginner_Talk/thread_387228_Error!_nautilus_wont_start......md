---
title: "Error! nautilus wont start....."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2007-03-18
i updated my ubuntu and im getting this error..........




after updating alot of things stoped working.............

how do i atleast make nautilus work again?

im using 6.06

---

### Post by taurus on 2007-03-18
Run it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
nautilus
```

---

### Post by L_o_N_e_R on 2007-03-18
umm it just sits there blinking.....

---

### Post by L_o_N_e_R on 2007-03-18
it took a while.....


```
 loner@loner-laptop:~$ nautilus

--- Hash table keys for warning below:
--> x-nautilus-desktop:///
--> file:///home

(nautilus:5653): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///home/loner/Desktop
--> x-nautilus-desktop:///
--> file:///home/loner
--> file:///home

(nautilus:5653): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time (keys above)

```

ok now what?

---

### Post by L_o_N_e_R on 2007-03-18
im getting this too.....

```
(nautilus:6285): Gtk-WARNING **: Self Mount Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Unmount Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Eject Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Format Volume: missing action

(nautilus:6285): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed

(nautilus:6285): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed

(nautilus:6285): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:6285): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:6285): Gtk-WARNING **: Self Mount Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Unmount Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Eject Volume: missing action

(nautilus:6285): Gtk-WARNING **: Self Format Volume: missing action

(nautilus:6285): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed

(nautilus:6285): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed

(nautilus:6285): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:6285): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

---

### Post by anaconda on 2007-03-18
how about reinstalling nautilus with synaptic..

or this could be a good time to try some other file managers.. have you tried:
konqueror, xfe or PCMan fm (my current favourite)

[http://pcmanfm.sourceforge.net/screenshots.html](http://pcmanfm.sourceforge.net/screenshots.html) 
there is ubuntu-package in the download tab.. it can be started from the terminal with "pcmanfm"..

---

### Post by L_o_N_e_R on 2007-03-18
> **anaconda said:**
> how about reinstalling nautilus with synaptic..

or this could be a good time to try some other file managers.. have you tried:
konqueror, xfe or PCMan fm (my current favourite)

[http://pcmanfm.sourceforge.net/screenshots.html](http://pcmanfm.sourceforge.net/screenshots.html) 
there is ubuntu-package in the download tab.. it can be started from the terminal with "pcmanfm"..



...wait i dont get it...what do i do?

---

### Post by anaconda on 2007-03-18
about which part..
to reinstall nautilus start synaptic, search for nautilus and right-click on it and select "mark for reinstallation" and select "aply"

to install xfe or konqueror just search them in synaptic and right click and select install and then aply..

to install pcmanfm go to the webpage and select download then select the "download deb package" under ubuntu and select the version and open with qdebi deb installer (default.. or download the package to your machine and dobleclick it to open qdebi..)..

then you might want to create a launcher for pcmanfm .. just right click on the desktop and select create launcher.. just type pcmanfm to the "launcher"..

---

