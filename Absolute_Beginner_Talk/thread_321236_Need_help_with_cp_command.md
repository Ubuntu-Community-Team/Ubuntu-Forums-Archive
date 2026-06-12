---
title: "Need help with cp command"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Dave54 on 2006-12-18
The theme I use doesn't carry over whenever I use "sudo ..." and I found the problem is that my theme is in "/home/dave/.themes" and not "/usr/share/themes".

So, I want to copy every theme from "/home/dave/.themes" to "/usr/share/themes". I can't edit "/usr/share/themes", so I'll have to use sudo and a cp command.

Can I use "sudo cp ..." to copy all the contents of "/home/dave/.themes" to "/usr/share/themes", and how do I do it?

(I tried to look for answers, but the recursively-overwriting-updatable-permissions-conflicting stuff scared me off)

Thanks,
-Dave

---

### Post by stsss8 on 2006-12-18
Press ALT + F2 to open up the 'Run Application' window. From there, type:
```
gksudo nautilus
```
This will bring up a root file browser, in which you will be able to copy the contents of your home folder to your usr folder.

Hope that I read your problem right and that this works. :)

---

### Post by bulldog on 2006-12-18
You can use ALT->F2 and type in the box ```
gksudo nautilus
``` to do it with the GUI.
You can do it with the terminal of course but I think this is more convenient for you.:D

---

### Post by Dave54 on 2006-12-18
Worked. Perfectly.

Thanks for the simple and fast response!

-Dave

---

