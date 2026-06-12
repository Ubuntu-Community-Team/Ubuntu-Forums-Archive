---
title: "Lost add/remove programms application"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by philgallagher on 2006-01-07
Hi all

Please be patient I'm very new and still now very little about Linux/Ubuntu.

I seem to have lost the add/remove programms option in applications and I have no idea why. I'm not aware of doing anything to it particularly but I may have done unknowingly. Can you tell me how to get it back?

Thanks folks

---

### Post by Susana on 2006-01-07
[QUOTE=philgallagher]Hi all

Please be patient I'm very new and still now very little about Linux/Ubuntu.

I seem to have lost the add/remove programms option in applications and I have no idea why. I'm not aware of doing anything to it particularly but I may have done unknowingly. Can you tell me how to get it back?

Thanks folks[/QUOTE]

Applications->System Tools -> Aplications -menu Editor

on right screen enable "Add Applications"

---

### Post by philgallagher on 2006-01-07
I tried that but the 'add applications' option is not there

Any ideas?

---

### Post by Susana on 2006-01-07
[QUOTE=philgallagher]I tried that but the 'add applications' option is not there

Any ideas?[/QUOTE]

hmm i don't know if this is the best option but you can create a new one.
In Applications menu editor select new entry. Name: Add Applications, Comment: Install and remove applications, Command: /usr/bin/gksu /usr/bin/gnome-app-install (this is how it is in my system but in brezzy it should be the same)

---

