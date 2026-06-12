---
title: "moving directories"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Majorflam on 2007-05-04
Hi, I would like some advice.

In Windoze, if I wanted to move a directory I would simply right click -> cut and then paste into new location.

How do I do this in Ubuntu?

---

### Post by octoberdan on 2007-05-04
I believe it is the same, if not similar, process. You can also try dragging the folder or Cntrl+x (cut) and then Cntrl+p (paste)

---

### Post by Majorflam on 2007-05-04
Hmm, it's working for some locations but not for others. I'm actually trying to move a html file into the xaamp htdocs folder, which is located at /opt/laamp/htdocs

Dragging and dropping is giving me a "permissions" error.

---

### Post by Majorflam on 2007-05-04
I hate to bump, but hopefully thi is a basic action and easily answered.

---

### Post by jfinkels on 2007-05-04
> **Majorflam said:**
> I hate to bump, but hopefully thi is a basic action and easily answered.

Some folders and files can only be edited/copied/moved by the super user, or "root user". To open a file manager session as the root user, type the following command in the terminal:
```

gksudo nautilus

```

However, it'll be easier for you to move stuff simply by using the command line in the terminal, like this:

```

sudo mv *folder* *destination*

```

---

### Post by jfinkels on 2007-05-04
More info on root user and "sudo" here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Majorflam on 2007-05-04
Thanks a million guys, I really appreciate it.

---

### Post by Majorflam on 2007-05-04
By the way, how would I make myself the owner of a particular directory, in order that I could write to that directory on a regular basis?

---

