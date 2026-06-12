---
title: "add and start an application"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by durus on 2007-01-15
Hi
I installed matlab today. I can start it from terminal by writing:
/opt/matlab/bin/matlab
how can i make it start only by writing matlab ?
How can i add it to my "start" menu ?

if i start matlab by "run application" (alt + F2), only the matlab logo comes up, but if i choose "run in terminal", it works. Is it possible to run matlab without having the terminal windows opened.

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Add the following two lines to the end of it.

```
PATH=$PATH:/opt/matlab/bin
export PATH
```
Save it.  Then, either log out and back in again or source it.

```
source ~/.bashrc
matlab
```

---

### Post by clint1010 on 2007-01-15
I cant remember what its called, but there is a menu setup tool, you can find it under "applications". See if matlab is listed there. Actually, as I'm thinking of it, it probably wont. Did you get matlab from the repos using synaptic?

---

### Post by durus on 2007-01-16
I installed it from a school cd.
About getting it to the menu, i remember that i have done it my self for another application by adding a file with information about it some where, but can't reamber how i did it.  

And do you know how do fix my biggest problem ? How to run matlab without having the terminal open ?

---

