---
title: "drag stuff to shortcuts?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-09-24
If I have a shortcut to the home folder on my desktop why cant I just drag stuff onto it from the desktop and it gets mooved to the home folder? Any way of doing this?

---

### Post by IYY on 2006-09-24
Yes there is. Go to gconf editor (it's supposed to be in Applications > System Tools > Configuration Editor, but might not be enabled by default so just run the terminal command **gconf-editor**.

In it, go to Apps > Nautilus > Desktop and check **Home Icon Visible**. Now you can drag and drop stuff into it. It's also possible to have a documents icon (if you create a folder /home/yourname/documents, functions like My Documents in Windows), trash, and mounted volumes (on by default).

---

### Post by altonbr on 2006-09-26
How do you do this is Kubuntu?

---

