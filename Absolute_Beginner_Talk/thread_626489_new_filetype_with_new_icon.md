---
title: "new filetype with new icon"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by mxsteini on 2007-11-29
Hi there,
I installed freemind on my system.
Now I want to associate the extension *.mm with the freemind-butterfly.
How can I do that?

---

### Post by CatKiller on 2007-11-29
Right-click on a .mm file.

Select Properties.

Select the Open With tab.

Click Add.

Select your application from the list, or if it isn't there, click on "Use a custom command" and type in whatever you would use to launch your program from the command line - usually the name of the application.

Edit:

The icon that gets used is determined by the them and MIME type of the file. I don't know how it works.

---

### Post by RomeReactor on 2007-11-29
Hi. You can right-click on a .mm file, select "Properties", go to the "Open With" tab, and press the "Add" button; if Freemind doesn't appear in the list, press "Use a custom command" and enter **/usr/bin/freemind-butterfly** (or the exact name of the executable, as found in it's correct location). To find out where that executable is, if you installed it from the .deb package [located here]("http://freemind.sourceforge.net/wiki/index.php/Download"), you can search for freeemind in Synaptic; once it shows up, select it and press "Properties", go to the "Installed Files" tab, and look for an entry in **/usr/bin**.

EDIT: Too slow.

---

### Post by mxsteini on 2007-12-12
Hi there,
sorry, I didn't ask correct.
I know how to associate files with programs.

I want to associate a file-type with an icon.

---

