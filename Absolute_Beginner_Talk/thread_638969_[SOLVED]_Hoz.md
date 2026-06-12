---
title: "[SOLVED] Hoz ?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-12-12
Alrighty guys and gals, here's my latest quandry.

Through Synaptic I installed a File Splitter/rejoiner by the name of 'hoz' which is the linux version of Hacha.
Looked in all menus, not to be found. Looked in the file system and found it and its' GUI, ghoz, under /usr/bin...
Clicked on the ghoz, which is supposed to be the gui for this prog. Nada,nothing,zilch.

Went back to Synaptic and uninstalled it thinking the rep might be corupt. Googled around and DLd the deb file for it. Gdebi put it back with the same results.

Everything, including the icon, is in the file system folder but she no workee...

Now my question is: How do you get a Linux executable to run when it dosen't want to be agreeable ?

Many thanks for any assistance,

Jon  :confused:

---

### Post by LaRoza on 2007-12-12
GUI programs usually are in "/usr/bin", but in "/usr/sbin".

Type "hoz" in the terminal.

---

### Post by spydon on 2007-12-12
You can also press alt+F2 and write ghoz or hoz or whatever program you want to run.

---

### Post by Romin-1 on 2007-12-12
Thanks guys, I got it all figured out.

This prog doesn't work as well as the parent prog, Hacha in Windows, and am now wondering if there is a sort of universal file splitter in the repos?

Once again, thanks,

Jon

---

### Post by jethro10 on 2008-04-06
I got it to work ok, it was just wierd it used

Cut --> splits file
Paste--> Joins files

What didn't work?

Jeff

---

