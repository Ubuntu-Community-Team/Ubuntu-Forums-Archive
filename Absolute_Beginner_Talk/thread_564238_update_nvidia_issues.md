---
title: "update nvidia issues"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-09-30
I am trying to update to the lastest nvdia and when i run sudo apt-get install nvidia-glx nvidia-settings i get the following error:

 nvidia-glx: Conflicts: nvidia-settings but 1.0+20060516-3ubuntu1 is to be installed

---

### Post by RyanZec on 2007-10-01
I tried to do a

sudo apt-get 1.0+20060516-3ubuntu1

but that just say that that package does not exists so i am totally in the dark with what 1.0+20060516-3ubuntu1 is.

---

### Post by Perfect Storm on 2007-10-01
nvidia-settings is included in newer version of nvidia, so you don't need to install it.

---

### Post by RyanZec on 2007-10-01
So my graphics driver should be update from the fresh install?  if so is there a good way to check to make sure?

---

### Post by Perfect Storm on 2007-10-01
```
nvidia-settings
```

---

### Post by RyanZec on 2007-10-01
I think when i tried that it gave me some type of error, i will let you know what it was whne i get home and try it again.

---

### Post by RyanZec on 2007-10-01
well i just did

sudo apt-get install nvidia-settings

instead of 

sudo apt-get install nvidia-glx nvidia-settings

and that works fine, thanks for the help

---

