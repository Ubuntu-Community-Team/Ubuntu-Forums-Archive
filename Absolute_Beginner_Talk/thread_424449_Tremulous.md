---
title: "Tremulous"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-26
i just downloaded the game and i get this error when i run the installer file:


Could not open the file /home/santanastown/Deskt…s-1.1.0-installer.x86.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

what should i do about this error

---

### Post by Benifited on 2007-04-26
how do i execute .run files?

---

### Post by taurus on 2007-04-26
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename.run**
sudo ./**filename.run**
```

---

### Post by chili555 on 2007-04-26
To run the installer, you really wouldn't open it with gedit. You need to make it 'executable' with:```
chmod +x whateverinstaller.run
```Then actually run it with:```
sh whateverinstaller.run
```Are you trying to do something different?

---

### Post by Benifited on 2007-04-26
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename.run**
sudo ./**filename.run**
```

thx alot bro

---

### Post by engla on 2007-04-26
Tremulous is in the repositories! Version 1.1! Try that before trying anything else, it normally installs cleaner :)
Good luck!

(Install package 'tremulous' with synaptic or other package manager)

---

### Post by Benifited on 2007-04-26
hey umm i just installed enemy territory and i have some mods for it but when i try to put the folders into the directory it tells me that i do not have permission.

what can i do so that i may put the files into the directory?

---

### Post by Sweet Spot on 2007-05-22
Using Taurus' method, I got Tremulous to install (thanks) but got a couple of error messages in the process. The first was when I typed in the final command before install:

> Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",

The second was after it finished installing: > Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.


Basically, I've no idea what either means. Is there something else I need to do at this point ? I have tested game play, and it seems to work fine, but have no idea as to what effect those errors might have in general. 

Any help appreciated.

Doug

---

