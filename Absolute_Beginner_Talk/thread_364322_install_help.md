---
title: "install help"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-18
After I install a package, how can I found out how to run it, if nothing new appears in my menu.  For instance, I just installed ace-of-penguins solitaire game, but there is nothing new in my games menu, so I have no idea how to run it.

Thanks

---

### Post by ramjet_1953 on 2007-02-18
Hi, Tim!

Quite often thise who create packages don't have the installer put an icon in the menu section. Why I don't know.

However, all is not lost. If you go back into the Synaptic Package Manager and do a search for the pacage that you just installed, right click on the package. A drop-down menu will open. Click on properties. Now a window will open. Click on the Installed Files tab and a list of files will be displayed.

Usually the program file will be uder /usr/bin or /usr/share/apps.

You may need to use the Nautilus file manager to navigate to this directory, if a symbolic link hasn't been set-up during installation.

However, in most instances just open the terminal and type in the name of the program and it should run.

You can also set it up yourself in the menu by using System>Preferences>Alacarte Menu Editor.

I hope this helps.

Regards,
Roger 8)

---

