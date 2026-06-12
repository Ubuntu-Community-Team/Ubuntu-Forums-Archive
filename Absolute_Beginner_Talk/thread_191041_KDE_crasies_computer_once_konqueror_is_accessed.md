---
title: "KDE crasies computer once konqueror is accessed"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by circadianhelix on 2006-06-07
Hoping someone can help with this.
I've installed the KDE packages through snaptic and as soon as I double click the konqueror icon the whole pc just freezes only able to power off.  
Any pointers appreciated.

---

### Post by aysiu on 2006-06-07
Try this terminal command: ```
mv ~/.kde ~/.kde_backup
``` Then press Control-Alt-Backspace to reset the X server and log back in again.

---

### Post by circadianhelix on 2006-06-07
That did the trick, thanks.

I'm assuming that changed the directories in some manner?

Also if its listed somewhere more or less obvious as an issue?

---

### Post by aysiu on 2006-06-07
Every application has a hidden folder (starting with a . ) that lives in your /home/username directory.

So basically that command just moved your /home/username/.kde configuration folder to /home/username/.kde_backup. The next time you started KDE, a new ~/.kde folder was created--a fresh one.

I've never encountered that error before, but I figured it probably had something to do with a corrupt profile.

---

### Post by nalmeth on 2006-06-07
wow great tip aysiu

---

