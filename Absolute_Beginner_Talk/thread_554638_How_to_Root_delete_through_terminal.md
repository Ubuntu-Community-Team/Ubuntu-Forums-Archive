---
title: "How to Root delete through terminal?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-09-19
Hi, i have a file in my home folder and im trying to delete it but it says i dont have the permission, and you know feisty doesn't allow you to login as root in the login manager, so how can i remove that folder and all of its contents?

---

### Post by justleen on 2007-09-19
```

sudo rm -r  /home/username/filename

```

if your really sure, use rm -rf  (f for FORCE, wont ask you anything, just permanently delete it)

---

### Post by jw5801 on 2007-09-19
Only use the -r option if you want to delete a directory. Also, if you're typing out the entire directory as above it's probably best not to use -r along with -f, if you accidently hit enter early, you might end up running "sudo rm -rf /home/" which will recursively delete the entire home directory without any user prompt at all.

Ubuntu doesn't enable a root login account by default as there's very little need for one, and preventing the existence of one greatly increases security!

---

### Post by justleen on 2007-09-19
> **kinngg said:**
> so how can i remove that folder and all of its contents?
:rolleyes:

---

### Post by bone2006 on 2007-09-19
I'd change the .bashrc and put in rm with -i for interactive, so if you press enter on accident it at least double checks with you.  Just change the alias of rm to equal rm with -i

---

### Post by jw5801 on 2007-09-19
> **justleen said:**
> :rolleyes:

Heh. Sorry I missed that bit.

---

### Post by hyper_ch on 2007-09-19
for removing an empty dir use:  rmdir directory

for removing a non-empty dir use: rm -R directory

---

