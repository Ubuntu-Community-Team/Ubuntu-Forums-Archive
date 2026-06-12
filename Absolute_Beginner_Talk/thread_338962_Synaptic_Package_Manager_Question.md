---
title: "Synaptic Package Manager Question"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-15
Hi all

I'm a real newbie (3 days experience and counting!) who likes chess. I've installed xboard and GNUchess on a fresh edgy installation. Both work fine. I'd like to try eBoard next as xboard is a bit basic. When i fire up Synaptic Package Manager and select eBoard for installation, I'm warned that 'the following action affects other packages. to be installed : gdk-imlib11, imlib-base, libgtk1.2, libgtk1.2-common and libungif4g'. Does this mean that I can install eBoard but not uninstall it without corrupting my system, as other files are overwritten, or can I always perform a complete uninstall and leave my system as it was? If I want to uninstall xBoard, should I do it before or after the eBoard install - or does it make no difference?

Sorry the question is so basic, but I'd appreciate any help anyone can give ;)

---

### Post by usien on 2007-01-15
i dont know what you mean by corrupting your system but as such there is nothing like corrupting your system in linux.what synaptic means to say is that these packages need to be installed in order for your required application to run, as it depends on them.you can safely remove any uneeded package later on.

---

### Post by willbur on 2007-01-15
Many thanks, usien. So you mean that the package manager will never overwrite existing code on my installation, and that the operation is always completely reversible?

I come from a Windows background where installers overwrite files without asking and often do not uninstall cleanly...

btw, do you know why Ubuntu has 2 package managers?

Thanks, once again :) 

willbur

---

### Post by Pobega on 2007-01-15
You can install it, all of those packages are just dependancies; Other packages needed to run.

For example, if you wanted to drink water you couldn't just drink it. You'd need a glass too. The glass is a dependancy of water.

---

### Post by usien on 2007-01-15
i know what you mean about windows.i was a windows user for about 12 years (used 3.1 to vista :)  ).there is a term 'dependencies' in linux.what it means is that almost all the packages (applications) depend on another package(possible a library), so to install a package you need to obtain its dependencies.synaptic checks to see if those dependencies are already installed on your system or not.it will only install them if they are not present(nothing is over written).everything can be safely removed and only those packages will be removed on which no other package is dependent.hope that helps somewhat.:-k

---

### Post by willbur on 2007-01-15
Many thanks, everyone - I really appreciate the help :D

---

### Post by willbur on 2007-01-15
OK fellas, I've installed eboard via synaptic, but I can't find it in my applications menu. Help! ;)

---

### Post by Pobega on 2007-01-15
Did you try running the command? Alt+F2 for the run menu, and type 'eboard'. If that doesn't work open a terminal and search for the command.

In a terminal when you type a letter and press tab, it will show you all of the possible commands. So you can always type "e" and look for something like eboard or eBoads (Capitalization counts!) or you can try "E" and look for "Eboard" or "EBoard". There's probably a better way but this is how I do it.

---

### Post by willbur on 2007-01-15
Thanks, pobega - alt f2 and eboard does the trick. Could you pls tell me how to add it to my 'applications' menu? Thanks

---

### Post by usien on 2007-01-15
usually applications are stored in the /usr/lib directory.find the file by the name of that command (could be in its own folder), create a shortcut to that file and place it in your menu.

---

### Post by willbur on 2007-01-15
Thanks again, usien - I owe you one!

willbur

---

