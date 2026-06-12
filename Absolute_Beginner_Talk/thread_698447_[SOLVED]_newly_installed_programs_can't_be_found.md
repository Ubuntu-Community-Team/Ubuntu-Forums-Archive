---
title: "[SOLVED] newly installed programs can't be found"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by kujaabi on 2008-02-16
Sometimes I install programs and then can't find them in the menus. They ARE intalled but I just can't fin them. I just installed simple backup, for instance, and can't find it anywhere. I don't know the name of the file so can't locate it. I've read through the other responses to this similar problem but they weren't much help to me re this particular problem.

---

### Post by zerhacke on 2008-02-16
Not every program has a gui.  If you apt-cache search XXXXX for whatever program sometimes the related matches are gui's for your program.

---

### Post by lluisanunez on 2008-02-16
Simple backup can be found in System > Administration menu
If it doesn't, you can edit the menus and add this two launchers:
[LIST]
[*]Simple backup config : gksu simple-backup-config
[*]Simple backup restore: gksu simple-restore-gnome
[/LIST]

---

### Post by kujaabi on 2008-02-16
I've checked all the menus. But don't see simple backup. I'm afraid I didn't quite understand what your suggestion was to do.

---

### Post by lluisanunez on 2008-02-16
Right-click on the menu icon > Edit the menus
You can create the menu items yourself. In the command field, put those two commands

That is, assuming simple backup was really installed

---

### Post by Omnios on 2008-02-16
Found with non complient menu entries I used to launch synaptic and looking up the package. Right clicking it you can choose properties and installed files. Here you can possibly find older non complient menu entries and also the bin files for the launch commands. Opening the menu file will give you the commands you need. also the bin files can give you the launch file name and also the path if needed. 

 Its dirty but it works.

---

