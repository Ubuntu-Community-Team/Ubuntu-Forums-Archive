---
title: "Questions about window display and deleting files"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-10-08
My first question is when I delete a file through nautilus in the /opt directory where does it go? I don't see it in the trash can and I do not want a bunch of delete files hanging around... ?

Second, when I  have a couple windows open and I launch let's say gedit it doesn't open in front of all other windows it seems to open behind the top window? Anyone else have a problem like this?

---

### Post by ThrobbingBrain66 on 2007-10-08
Depending how you deleted them, they may either be gone for good, or in /root/.Trash

Do you have Beryl/Compiz/Fusion enabled?  There is a "focus stealing prevention" option in the settings manager.  You'll need to change that to a lower setting.

---

### Post by Shazaam on 2007-10-08
1. Are you running as root? Look in /root/.Trash (see the period before Trash? Hidden file).
2.Mine does that too, haven't figured that out yet but it's probably something simple.

---

### Post by cjnkns on 2007-10-08
1) I am logged in as a regular user not root. I looked for a root/.Trash but haven't found it yet maybe I am doing something wrong guess I'll keep looking

2) no i do not have any of the eye candy stuff instlalled so not quite sure why the window displays the way it does.

If the files are gone for good that's fine -it'd be nice to know in case I accidentally delete something I want to get back.

---

### Post by Shazaam on 2007-10-08
Crtl+H shows hidden files in Nautilus.
The . before a folder or file makes it hidden ie  root/.Trash

---

