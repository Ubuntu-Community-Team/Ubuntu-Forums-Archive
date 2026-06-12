---
title: "Beryl Super Key Issue"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by jpoRS on 2006-12-21
Hey

I am running Beryl on my hp, not using it for too much, its just eye candy.  I have the super key/the windows key set to open a terminal.  It still works fine in Metacity, but when I switch over to Beryl it doesn't respond.  I have changed all of the Beryl shortcuts to not include the super key, and still nothing.  Its not a big deal, I do most of my work in Metacity, its just a nuisance more than anything.

Thanks
jim

---

### Post by JayTee on 2006-12-21
You can use Beryl Settings Manager to set shortcut keys for programs when running Beryl.
Open Beryl Settings Manager and choose General Options on the left side. On the right side click on the keyboard tab and scroll down until you see entries that are titled Run command 0, Run command 1, etc. As an example I have the gnome-terminal set to launch when I click Alt +t combination so configure Run command 0 to use those keys then click on the Commands tab and under Command line 0 enter gnome-terminal. The current version of Beryl on Dapper that I'm running now which is version 0.1.1 allows for 11 custom commands. 
If you switch back to Metacity at any time the normal Gnome shortcuts will work as you've configured them to. Since Beryl replaces Metacity when running in Gnome it hooks all the keyboard events instead of Metacity so the Metacity shortcuts won't work in Beryl.

---

### Post by jpoRS on 2006-12-21
Yep, that fixed it.  Thanks a lot!

Happy Holidays
jim

---

