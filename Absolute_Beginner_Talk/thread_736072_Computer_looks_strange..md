---
title: "Computer looks strange."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by asdfqwert on 2008-03-26
Well i installed the GNOME compiz manager, and the emerald theme manager.

This morning the monitor wouldn't get out of sleep mode so i restarted the computer.

Well when i logged in the GNOME compiz manager said it 'couldn't start succesfully' or something like that,and i can't access synaptic because my user password won't work anymore. In addition, synaptic now has this "remember password" option.

And finally, ubuntu now has VERY small fonts,(not only on firefox) and instead of having an orange human theme bar for my windows, it's red.

Please see the screenshots.

---

### Post by LowSky on 2008-03-26
looks like Emerald is running to turn it off, go to terminal and trye
 ```
metacity --replace
```

see if that fixes thing for the time being

---

### Post by kolisikepu on 2008-03-26
Did you change any settings in Compiz or Emerald?  What happens if you change theme?  Have changed anything in Appearance Preferences Font tab?

---

### Post by Google Spider on 2008-03-26
I am not sure but maybe a driver issue ? What graphics card do you have ?

---

### Post by asdfqwert on 2008-03-26
When i run that metacity --replace command i get 

> ubuntu1@ubuntu1-desktop:~$ metacity --replace
Window manager warning: 0 stored in GConf key /apps/metacity/general/num_workspaces is not a reasonable number of workspaces, current maximum is 36
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
^[      ^[      Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed





And if i go back to human, there aren't any close/minimize/maximize butotns on the windows and avant windows manager won't start up.


Also, synaptic STILL doesn't work :P

Things seem to be running EXTREMLY slow now too.

AND alt+tab won't work.

---

### Post by kpkeerthi on 2008-03-26
Turn off Visual Effects in System -> Preference -> Appearance -> Visual Effects

---

### Post by asdfqwert on 2008-03-26
It is.

---

### Post by inksmithy on 2008-03-26
Looks like something has gone wrong in X. Do you have another session you can use while you try to figure it out?

---

### Post by asdfqwert on 2008-03-26
How do i use another session?



Fixed the password problem.


Also, the GNOME error was

> The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.



Nautilus has been completly changed, and it's hard for me to use it.(opens folders in a new window)

---

### Post by asdfqwert on 2008-03-27
BUmp.


The update manager now says i have updates, but when i click on install, it just checks for updates, but doesn't install them.

---

### Post by asdfqwert on 2008-03-30
bump.

---

