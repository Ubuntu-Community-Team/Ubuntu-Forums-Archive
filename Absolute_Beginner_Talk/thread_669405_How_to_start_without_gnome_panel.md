---
title: "How to start without gnome panel"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Faud on 2008-01-16
How do I make it so that when I start up there are no gnome- panels on my desktop ? I would like it so that I have to open up a terminal and actually type gnome-panel for it to pop up. 
Thanks

---

### Post by NilsE on 2008-01-16
I am not sure how to do that but maybe a compromise would be to hide them unless moused over.

---

### Post by Faud on 2008-01-16
Would you be able to write something like
```

#!/bin/bash
 &&
gnome-session-remove gnome-panel

```
or do you think that would hurt something ?

---

### Post by cmittle on 2008-01-16
You could install fluxbox (which loads almost instantly after you login).  After installing fluxbox it should appear as an optional session type when the login screen appears.  Fluxbox is my preferred windows manager now.  You can modify the contents of the .fluxbox/menus file to make as many or as few programs appear upon your right mouse click.  You can also modify the contents of .fluxbox/keys file to make as many keyboard shortcuts as you want (e.g. Alt+f launches firefox, Alt+t launches xterm, Alt+F4 closes the active window).

---

### Post by Faud on 2008-01-26
Ive been looking into fluxbox and Ive liked what Ive seen so far. If I install it will I still be able to set it up to get notifications on software updates in the repos ?

---

### Post by belda on 2008-02-21
to completely remove it (in casu you want to use something nicer like kiba-dock or avant-window-navigator-bzr ) you can
You can totally hide Gnome Panel. Follow the procedure below::
1. In Terminal, give "gnome-session-properties" command.
2. Choose "Current Session" tab.
3. Click on "gnome-panel" and click remove.
4. Press alt+F2
5. On the properties do apply and close.
6. Close all programs that you don't want to run on startup
7. In the run dialog give "gnome-session-save".

this will completely disable the gnome panel, but mind, that you need to have ways of logout, run somthing, etc...

---

### Post by Trail on 2008-02-21
About what belda said... That does not "remove" it but stopping it from getting loaded while booting.

I set up AWN once and wanted the gnome panel out of the way, so i tried removing it with aptitude. Turns out that some libraries or applets (I don't remember) were needed by AWN so as to display the file browser and stuff like that.

In practice what I did to keep gnome-panel and preventing for loading completely (I had issues with the abovementioned method) was to rename the executable. You can find the executable location with the command "which gnome-panel" and rename it to, say, "gnome-panel2" with the "mv" command. Then rename it back up if you want to undo the changes. Not very elegant, but it worked.

---

