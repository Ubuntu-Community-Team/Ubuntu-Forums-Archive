---
title: "how can i make a keyboard shortcut for system monitor (ctrl alt del)"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by bishop9226 on 2007-05-30
i want sys monitor to open up when i hit ctrl alt delete, thanks

---

### Post by sankarv on 2007-05-30
just an idea. dont know how it would help...


goto

gconf-editor 


and in the global_keybindings see if u could add one for 'gnome-system-monitor'.


or possibly u could browse through the .gnome/* files in your home and find where keybindings are defined.


u could also try with gconf-tool2

---

### Post by userundefine on 2007-05-30
Automatrix has this feature exactly.  I'm not sure how to apply the tweak without it, though.

---

### Post by bishop9226 on 2007-05-30
thanks. automatix one doesnt work in beryl though, only metacity. i got it to work in beryl through beryl manager

for anyone else who wants to do it:

To configure it in beryl first open the beryl settings manager. Then select the commands tab and go to command 9. Set this command to gnome-system-monitor. Then next you will go to shortcuts>commands and set run-command 9 and add <Control><Alt>Delete. After this just close the beryl settings manager and you will have the function enabled.

---

### Post by medley on 2007-05-30
> **bishop9226 said:**
> i want sys monitor to open up when i hit ctrl alt delete, thanks


I created a shortcut for system monitor, but I use ctrl-alt-p (for performance monitor) because ctrl-alt-del is already mapped. You can create a shortcut by making sure your task panel is unlocked (right click and unlock), then right clicking on your 'K' or whatever you use that equates to 'start' in Windows. Select edit menus, then navigate to 'system performance monitor' and you'll see at the bottom that you can map a shortcut. Select 'save' at the top and you should be done. You probably want to lock your panels again.

---

