---
title: "Adjusting the mouse double-click for gtk apps"
date: 2014-11-02
forum: Assistive Technology &amp; Accessibility
---

### Post by vasa1 on 2014-11-02
A double-click with the mouse is two single clicks within a certain interval. If the interval is too short, some people may have difficulty in double-clicking.

The interval can be adjusted for gtk2 and gtk3 apps and possibly for your window manager.

**For gtk2 apps**:

You may have a pre-existing text file called ~/.gtkrc-2.0. It should have a line like this:
```
include "/home/your_login_name/.gtkrc-2.0.mine"
```If such a line doesn't exist, add it at the top of the file. Save the file and exit the editor.

If you don't have ~/.gtkrc-2.0, create it with a plain text editor and only add the same line and save the file and exit the editor.

Next, create the plain text file called /home/your_login_name/.gtkrc-2.0.mine. In this file, add this single line:```
gtk-double-click-time=1000
```Save the file and exit the editor. What this line tells gtk2 apps is to consider two clicks within 1 sec (1000 milliseconds) as a double-click. If you don't like 1000, replace it with a lower value.

All gtk2 apps opened subsequent to editing and saving .gtkrc-2.0.mine will accept the new double-click interval.

**For gtk3 apps**:
See if /home/your_login_name/.config/gtk-3.0/settings.ini exists. If it doesn't exist or the gtk-3.0 folder doesn't exist, create the folder and file as needed. If settings.ini exists, add this line:```
gtk-double-click-time=1000
```to the end of the file using a plain text editor. Save and exit the editor.

If settings.ini doesn't exist, copy over the file of the same name from /etc/gtk-3.0 and then edit the file to have the line above.

**For your window manager**:
My window manager, Openbox, can be set to maximize a window by double-clicking in the title bar or to "roll up" (or shade) a window. Here too the double-click interval can be set. I would expect that other window managers have something similar.

The above obviously is user-specific. I think if one wants system-wide changes, one could edit /etc/gtk-3.0/settings.ini and /usr/share/chosen_theme/gtk-2.0/gtkrc.

---

### Post by ajgreeny on 2014-11-02
I am interested to know why you have chosen to do it this way, when most,  if not all DEs (I haven't used them all) have a graphic mouse configuration utility which can be used to do the same thing.

It does give some very interesting and possibly useful background information, I agree. 
Perhaps this is just for gtk apps if you want any qt apps to have a different mouse setting?

---

### Post by vasa1 on 2014-11-02
Yes, this expressly is for gtk. I don't know much about qt apps.

Re. doing it this way rather than via a GUI, I've just been doing it this way. No other justification :)

---

