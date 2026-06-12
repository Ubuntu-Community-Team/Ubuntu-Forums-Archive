---
title: "Gnome error on startup"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by prodigy_00 on 2007-07-15
I keep getting this error every time I start up in Gnome: 

An error occurred while loading or saving configuration information for gnome panel. Some of your configuration settings may not work properly.
Type mismatch:Expected 'string got' got'int' fpr key /apps/nautilus/desktop/computer_icon_name

What can I do?

---

### Post by ThrobbingBrain66 on 2007-07-15
Hit Alt+F2 and type gconf-editor in the box.
In the left-hand pane, navigate to the path as described in the error message (/apps/nautilus/desktop/computer_icon_visible). Right-click the computer_icon_visible key and choose 'edit key'. Change the type from integer to string.

---

### Post by prodigy_00 on 2007-07-15
thanks that worked!

But I'm still having more problems with Gnome. No icons appear on the desktop, my wallpaper always turn black after I login, and I can't right click on the desktop. Can you help me with these or should I create a new thread?

---

### Post by ThrobbingBrain66 on 2007-07-16
When that happens hit Alt+F2 again and type 'gnome-settings-daemon' (without the quotes) and see if that helps

---

### Post by prodigy_00 on 2007-07-16
nothing happens if I try to run it

---

### Post by ThrobbingBrain66 on 2007-07-17
Your problem wasn't what I thought it was then, you might want to make a new thread.

---

### Post by tille on 2007-08-04
Thanks, i had the problem too. I had to run gconf in sudo through the terminal to change the type to "string". But thank you! :)

---

