---
title: "easier way to open flock browser?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by eekbot on 2007-01-05
is there a way for me to create a panel shortcut for flock (a web browser)?

currently, i have to go into the directory where i extracted flock to open it, but this can get tedious.

i also tried to make a shortcut, by doing:
ln -s flock ../..

and it creates a broken link.  would you please tell me an easier way to open flock?  thanks!

---

### Post by jvc26 on 2007-01-05
Right click on the top bar,
Add to panel
Custom Application Launcher
Name: Flock
Command: Browse to where you launch it from and select the launcher.
Then close and try it out :)
Il

---

### Post by eekbot on 2007-01-05
ooh lala!  worked like a charm!  thank you very much. :D 

but regarding my attempt to create a shortcut...  do you know why it creates a broken link?

---

### Post by jvc26 on 2007-01-05
Not honestly sure but, looking at the manual:
```

SYNOPSIS
       ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
       ln [OPTION]... TARGET                  (2nd form)
       ln [OPTION]... TARGET... DIRECTORY     (3rd form)
       ln [OPTION]... -t DIRECTORY TARGET...  (4th form)

```
Do a:
```

man ln

```
in terminal and that will show you how the ln command works. I think it may be to do with your option -s and the order of putting flock and the /path/to/flock
Also your ../.. was that as in /path/to/flock or was it literal in ../..?
Hope that helps,
Il

---

