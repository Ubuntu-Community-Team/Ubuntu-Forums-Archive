---
title: "Cleaning Wine Folder"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Gatchaman on 2007-06-05
Ive unistalled several windows programs in WINE, but their program folders remain in the Wine/Programs folders.  What&#347; the easiest way to remove these orphan folders?

Thanks in advance for the help!

---

### Post by vanadium on 2007-06-05
Highlight the directory and press the delete key.

If you want a brand new "Windows" wine install, delete your hidden .wine folder. The next invocation of wine will recreate a brand new wine system for you.

---

### Post by Gatchaman on 2007-06-05
> **vanadium said:**
> Highlight the directory and press the delete key.

If you want a brand new "Windows" wine install, delete your hidden .wine folder. The next invocation of wine will recreate a brand new wine system for you.

Thanks for the quick response.  I tried using the ¨delete"key after highlighting the folders on my Thinkpad T30, and nothing happens.

---

### Post by vanadium on 2007-06-05
Quite strange. Did you effectively browse into the "~/.wine/drive_c/Program Files"? For me, all the directories under Wine are owned by me as user with read, write and execute rights. Deleting a directory from Nautilus should thus work.

Can you post the output of the following command (literaly):

> 
ls -l /home/$USER/.wine/drive_c/Program\ Files/


This will list the contents of that folder along with the permissions.

---

### Post by _davenc on 2008-01-24
If you can't get rid of deleted program links under the applications~wine drop down menu, go to /home/$user/.local/share/applications directory and delete the wine folder.

---

