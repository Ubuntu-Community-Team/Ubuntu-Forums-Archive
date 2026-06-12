---
title: "Help with gui sudo"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Jjohn on 2007-04-10
Hi Folks
              Will someone please remind me what I need to write in terminal to get full root powers on the desktop I want to point and click some files to different directories...:)

---

### Post by justleen on 2007-04-10
if you start the terminal as a user ```
 sudo <command> 
```
that runs a command as root.
to get a "root session" ```
 sudo -i 
```

if you need it more often, create a new launcher, and add the command ```
 gksudo gnome-terminal 
```


edit: duh, you need a root nautilis
from a terminal : ```
 sudo nautilus & 
```
or create a luancher to gksude nautilus

---

### Post by heimo on 2007-04-10
Should be:
```
gksudo nautilus &
```


:)

---

### Post by Jjohn on 2007-04-10
Many thanks People...:)

---

