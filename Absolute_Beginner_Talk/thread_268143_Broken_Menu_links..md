---
title: "Broken Menu links."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by maaronB on 2006-09-29
I have just downloaded GtkOrphan, and without bothering to read about it or figure out how it worked I decided to use some of it's automatic features to clean up my system.  The result of this "brillant" plan is that it completely removed many programs from my system.

The problem is that it removed the programs but did not remove them from my menu list.  So the programs are not installed they don't show up in the Alcarte Menu Editor.  The only way that works for me to remove the broken links is to redownload the programs then reunistall them.  But this obviously takes a long time, and seems horribly unefficient.
 
So my questions are.
1. Is there anyway to undue what GtkOrphan has done.
2. How can I manually edit the Menu.
3. Is there a automated script that will remove broken links from the menu for me.

---

### Post by baldy1324 on 2006-09-29
gnomes application menu reads .desktop files in the /usr/share/applications directory. these files have the command that it runs, icon... i gues GTKOrphan didn't remove these file so... ```
cd /usr/share/applications
```. then ```
rm file.desktop
``` this will remove the menu entry. ```
sudo killall gnome-panel
``` this will refresh the gnome-panel and voila

---

