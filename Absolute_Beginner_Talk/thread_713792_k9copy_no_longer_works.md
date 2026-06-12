---
title: "k9copy no longer works"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by agentsmith23 on 2008-03-03
I was attempting to change some settings in K9copy and now it won't work at all. When ever I try to start the program it just begins to load and then crashes and brings up the KDE crash handler screen. I have tried uninstalling and reinstalling the program but it just keeps happening. Is there a file I can delete or a way I can just reset the settings in K9copy? I know I changed two settings, one was to make it burn automatically rather than ask for a dvd each time and I can't remember what the other option was. 

Please help!!!


I just tried something new. I can run k9copy using su and it works perfectly. How do I get it to work under my default account?

---

### Post by Arthur Archnix on 2008-03-03
open a terminal and type 
```
k9copy
```
If it crashes it should spit out some error messages into the terminal that will help figure out what's wrong.

---

### Post by agentsmith23 on 2008-03-03
Now i remember what the other option I changed was. It had to do with the preview being rendered using opengl. I selected that option just to see if it would make difference. I guess it did make a big difference. Does anyone know how to fix this? 

Here is the error message I got from the console.

dnd@dnd-desktop:/$ k9copy
kbuildsycoca running...
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
KCrash: Application 'k9copy' crashing...

---

### Post by 3rdalbum on 2008-03-03
To delete the preferences, remove the file ~/.kde/share/config/K9Copy

Like this:

```

cd .kde/share/config/
rm K9Copy
```

The same principles apply for deleting the preferences of any other program - they are always stored in hidden files or hidden directories inside your home directory.

---

### Post by agentsmith23 on 2008-03-03
Thank you so much! That worked perfectly!

---

