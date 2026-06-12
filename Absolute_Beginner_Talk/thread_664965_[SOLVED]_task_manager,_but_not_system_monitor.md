---
title: "[SOLVED] task manager, but not system monitor"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by matjaz on 2008-01-11
Hi,
I would like to know if there is some sort of an advanced task manager for ubuntu.
Something like Sysinternals process explorer- somthing that lets you see which process is using which port, which files are opened by some process, ... stuff like that.

I have read the posts that say if you want a task manager use system monitor.

I would like to see which process uses which port and i can't get this in system monitor.

I would appreciate if there is a terminal command that would tell me that, if there is no programm that would display that info in a process-explorer way.

Thanks 

Matjaz

---

### Post by eapache on 2008-01-11
Try the command "top". I'm not sure how advanced it is, but it is the default task manager for the command line.

---

### Post by matjaz on 2008-01-14
Thanks for letting me know the exisistance of top, i am sure it will come in handy once.

In the mean time, i have discovered that Firestarter can tell me which apps are using which ports, though it doesn't display that info for all apps ( for some it just says "unknown". Perhaps it has something to do with how the apps were run - mybie it doesn't get the names of those that were ran by a superuser? Don't know... ).
And there is Ethereal too...

Matjaz

---

### Post by fiddledd on 2008-01-14
You might want to try htop, I think it's in the repositories, it might suprise you. :)

---

