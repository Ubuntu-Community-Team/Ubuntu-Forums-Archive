---
title: "Edit the menu, so a program always starts as root"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Mudkip on 2008-02-18
Hi,

Im kinda new to linux, and im trying to edit the menu, so it always starts a application with root access.
(The Applications -> delopment -> eclipse one)

I need this, because without root access, eclipse cant write to the apache root directory
And, its kind of annoying to have to start eclipse with the terminal every time...

So.. how do i do this? 

Thanks

---

### Post by smartboyathome on 2008-02-18
Just right click on the menu, select edit menu, navigate to Development on the sidebar, and double click Eclipse One. Then, put before the command gksu. Now it will run as root.

---

### Post by sabatron on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=17728]("http://ubuntuforums.org/showthread.php?t=17728")

if I understand you correctly, the this thread will help you create a launcher

---

