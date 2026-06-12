---
title: "Help Finding certain programs"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Nazty_Nayt on 2008-01-31
OK, gotta noob question.  I'm trying to fix my flash player for firefox, and apparently I have to run a command through the terminal example; /usr/lib/mozilla-firefox and I know that's just an example, but I cannot figure it out, the user I'm assuming would be my name that is the sudo user, but as for this lib folder I have no idea what that is, and I have no idea where my firefox browser is kept, it's just in the tray.  Can anyone help me?

---

### Post by Ainab on 2008-01-31
user is the root user (administrator) and to find out the location type locate flash.

---

### Post by ispy on 2008-01-31
did you try (re)installing the necessary plugins within firefox?

otherwise, you can try going to Applications>>Add/Remove>>and search for the macromedia flash plugin and reinstall it from there. the terminal gets confusing if you don't understand what you're doing, that's what GUIs are for.

---

### Post by spiderbatdad on 2008-01-31
In your example /usr/lib/mozilla-firefox  would be a directory or folder in your file system. You can navigate through the file system by selecting Applications>>Places>>Computer>>File System...it would be handy to add the file system icon to your panel. Once you know the "path" to a file you would edit the file by entering commands in the terminal to open a text editor with the path to the file.
Text editing files other than those in your home directory does require sudo permission.
So, if I wanted to edit /boot/grub/menu.lst. I would open the terminal and type:```
gksu gedit /boot/grub/menu.lst
```gedit is the gnome graphical text editor. gksu is a command to open a graphical application with sudo permissions. Once I complete the editing, I save with the save option in the window and close all applications.

---

### Post by Nazty_Nayt on 2008-01-31
> **ispy said:**
> did you try (re)installing the necessary plugins within firefox?

otherwise, you can try going to Applications>>Add/Remove>>and search for the macromedia flash plugin and reinstall it from there. the terminal gets confusing if you don't understand what you're doing, that's what GUIs are for.

I can't uninstall macromedia, it won't let me unclick the check box.  And I know the terminal is extremely confusing, sometimes I have no clue what people are talking about when it comes to the terminal.

---

