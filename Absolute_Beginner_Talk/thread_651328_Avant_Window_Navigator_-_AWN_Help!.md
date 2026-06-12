---
title: "Avant Window Navigator - AWN Help!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-12-27
Hi folks,

I am a total noob.  I cannot figure out how to even install AWN.  Every time I try something, it goes wrong.

For instance, when I try to install it in the terminal, I add the source repositories (I think) and then type sudo apt-get install avant-window-navigator and I always get "Package not found" or something like that.

I also tried downloading a .tar package and then extracting it, but when I typed "make" it said something like "no make command found" (even though when I typed ls to show me what was in the package file, there was a make).

I have tried these different things, but I'm sure I'm making some total noob mistake.  I try to make sure I'm not missing a step or anything, but I must be doing something wrong.

Please help.  I'd really like to add the AWN dock to my desktop.

Thanks,
awiggin

---

### Post by awiggin on 2007-12-27
Help.  :)

---

### Post by rune0077 on 2007-12-27
To run the make command, you need to be sure that you're in the same directory as the make-file. So "cd" to the directory where you extracted the .tar to, and then run the make and make install files.

---

### Post by lswest on 2007-12-27
to make anything you need the build essential package which you can install with ```
sudo apt-get install build-essential 
``` and for avant-window-manager try doing ```
apt-cache search avant window manager 
``` and copying & pasting the package name from there, and if there are no packages found, the repository is missing, and so you'd have to get that repository.  Try the other 2 ways first though.

---

### Post by seventhc on 2007-12-27
I believe it is also in synaptic package manager....system>administration>synaptic package manager, then you click on the binoculars and do a search for avant window manager, it'll cure what ails ya. :D

---

### Post by awiggin on 2007-12-27
I got it downloaded.  Thanks for the help.

I don't know how to customize the AWN dock, though.  Any help there?  I don't want it to look like the junky dock.  I like the one that looks like it's sitting on a reflective table.

Thanks if you can help.  Otherwise, don't worry.

-awiggin

---

### Post by rune0077 on 2007-12-27
Go to System > Preferences > Awn Manager.

From here, go to the Bar Appearance tab, and from the Look dropdown menu select 3D look. That should be it.

---

### Post by lswest on 2007-12-30
or you might just have to install a new theme for it, but that can be done by choosing install new theme (after having downloaded a suitable theme) and installing the theme, in the same menu as the one described above.

---

### Post by JillSwift on 2007-12-30
Here's a very nice guide to installing AWN:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by awiggin on 2008-01-01
Hey all,

Thanks for all the great tips.  With your help and guidance, I was able to get this all fixed.

My AWN is installed and working well.  

You all are what I love about the Linux / Ubuntu community.

Peace,
awiggin

---

