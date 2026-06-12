---
title: "Synkron - hidden GUI"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by netpage on 2008-03-05
I have installed Synkron and using the GUI I set it to be 'hidden' [an icon in the top panel] but now I can not access the GUI.  I have tried un-installing the program, but as soon as I re-install it [even after a computer restart] it remains as an icon in the top panel.

This is a bit too Windowsesque for my liking :(

If this was Windows I would edit the registry and all would be OK.  What is the equivalent for Ubuntu?

Thanks

James

---

### Post by DieB on 2008-03-09
there are two possiblities:

1. the user configs are located in hidden folders (those starting with a dot) in the home folder you can make them visible through [Ctl+H]. there i would search for somethin with a ".conf" at the end look the file up in gedit (texteditor) and change. 

2. somethin like your registry and here are the settings for most applications: it's "gconf-editor" in a terminal, or setten the icon free for applications menu by changig it inside of "MainMenu" in the System-Menu

hope it helped

---

### Post by netpage on 2008-03-10
Hi DieB,

Thanks for your post.  I also got this info from the Sourceforge.net site and have managed to edit the configuration file.

> To remove all settings for Synkron, go to ".config" in your home directory (note that this is a hidden directory, so you need to enable something like "show hidden files" in your file manager) and remove the folder named "Matus Tomlein". That should do it. 

All I need to do now is learn how to compile programmes so I can install version 1.2.

Cheers

James

---

### Post by DieB on 2008-03-10
well it is:
 untar the package "cd" (changedir) into it and then (in general) type:

./configure
make
sudo make install

that's it as said in general some work different, but the project-pages normally tell you how to compile their packages

---

