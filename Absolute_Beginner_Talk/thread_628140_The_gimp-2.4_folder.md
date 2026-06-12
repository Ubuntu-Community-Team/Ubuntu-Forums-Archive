---
title: "The gimp-2.4 folder"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-11-30
Hi,
At this page [http://docs.gimp.org/en/gimp-concepts-setup.html](http://docs.gimp.org/en/gimp-concepts-setup.html) of the GIMP manual they mention a directory which if deleted can reset the configuration of GIMP as if it is starting for the first time.  I cant find it in my home directory (using 7.04).  Does this folder exist in Ubuntu?

---

### Post by Halfling Rogue on 2007-11-30
It should, but it's hidden. You have to go into terminal, go to your home directory ( "cd /~" ), and type "ls -a". It should be there as .gimp-2.4. If you want to delete it, type "sudo rm -rf .gimp-2.4".

---

### Post by SteelCore on 2007-11-30
That did work.  Thank you.

---

### Post by cyberbuff on 2007-11-30
Or you can just hit CTRL+H to view the hidden files and folders

---

