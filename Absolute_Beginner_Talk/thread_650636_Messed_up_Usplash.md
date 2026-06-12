---
title: "Messed up Usplash"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Finaltheorem47 on 2007-12-26
I was trying to change my Usplash and was following a guide on how to do it.  I put the new .so file in the root directory and installed start up manager to be able to set the new usplash as my default one.


It didn't work and it kept booting the original one, so I read somewhere to chance the name of the new one to the name of the original boot one, so I did that exactly and now both boot screens appear in startup manager, but when i select one, exit, and come back it keeps reverting to a blank option, and when I boot it, only text appears.


I tried installing another program that does the same thing, and when I started it up, it came back with an error message saying I have no usplash themes.  What did I do wrong and how can I fix it and put it to the Usplash theme I want.  This was I think #1 or #2 on most popular on gnome-look so I doubt its a broken one.



Thanks!

---

### Post by Finaltheorem47 on 2007-12-26
Bump, was on second page

---

### Post by spiderbatdad on 2007-12-26
what I have done to install usplash themes is to unpack the tar to my desktop then using sudo mv the directory to /usr/share/gdm/themes.  You can also open the gui login windows
preferences and choose the local tab, then drop the directory into it. If you boot into gnome failsafe i think you can reset your usplash till you fix the problem. The theme directory contains a number of files and I wouldn't recommed renaming them unless you know what you're doing. Some of the file names are specific and duplicating file names can cause problems. Sometimes the GreeterGDM.Desktop theme does wierd things if permission are changed.

---

