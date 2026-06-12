---
title: "gksudo natalist problems.. should be easy for yall to help"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-04
Two things..

when i say gksudo nautilus the terminal says this..
"(nautilus:6486): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."
 

yet the nautilus window pops up fine and everything..


the second problem is that when i issue that command via a launch i want the command window to go away.. is there a special command to hide the command window afterwards?

---

### Post by podunk on 2006-10-04
It's a reported low priority bug - just ignore it. :-)

To hide the terminal - click the minus sign and send it to the task bar? Maybe I don't understand your question, if not i'm sorry.

---

### Post by systemintheglitch on 2006-10-04
Are you serious.. Its quite annoying.. 

Is there at leaste a way to hide the console after the program is launched?

---

### Post by systemintheglitch on 2006-10-04
> **podunk said:**
> It's a reported low priority bug - just ignore it. :-)

To hide the terminal - click the minus sign and send it to the task bar? Maybe I don't understand your question, if not i'm sorry.


You know.. send it to the background as if its not even there.. Not even on the taskbar.. Its purpose it complete, it launched my program now it can go die.

---

### Post by aysiu on 2006-10-04
How about Alt-F2 ```
gksudo nautilus
``` or just creating a launcher or keyboard shortcut for ```
gksudo nautilus
```?

If not, you can also try ```
gksudo nautilus &
```

---

