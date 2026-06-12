---
title: "Install/Uninstall"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by paritosh1010 on 2006-12-26
I had the search utility which comes with GNOME by default. Then, I installed Beagle from Automatix. I didnt like it, since it searched only places which were indexed(this is weird- it can take its time to search the whole filesystem if I ask it to..?) so I uninstalled it using Automatix, but the uninstall was not complete. Now, I havent got my original search program back, since the menu is still linked to the beagle program. Can anyone tell me the exact path for the GNOME search program, and some better searching program?

---

### Post by bruenig on 2006-12-26
Some ways to search via command line.

whereis whatever - this will search within the PATH

locate whatever - pretty expansive search, the one I generally go with

sudo find / -iname whatever - not sure what the difference is but it searches.

---

