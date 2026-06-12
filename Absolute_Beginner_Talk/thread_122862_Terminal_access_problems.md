---
title: "Terminal access problems"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-01-28
For some unknown reason, I receive this response when I try to access terminal:

"Cannot launch entry

Details: Failed to execute child process "Terminal" (No such file or directory)"

I'm trying to configure WINE without much luck when this cropped up.

Thanks for the help.

---

### Post by agapito on 2006-01-28
You could try Alt+F2 to open the Run Application dialog  and there type gnome-terminal and run it. Does this work?

---

### Post by Cousindaddy on 2006-01-28
Yes, this brings up a small "Run Application" window.  How may I correct the problem with accessing terminal from "Applications" -> "System Tools?"

---

### Post by agapito on 2006-01-28
Probably there's something wrong with the menu shorcut. Use Applications-> System Tools -> Applications Menu Editor  and edit it. Change it to *gnome-terminal --working-directory=%f*

---

### Post by agapito on 2006-01-28
By the way, you can have a "open terminal" option in the nautilus' right click menu if you install *nautilus-open-terminal*
Do do this use synaptic or do
*sudo apt-get install nautilus-open-terminal*
It great!

---

