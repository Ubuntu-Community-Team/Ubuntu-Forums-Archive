---
title: "Terminal not saving changes"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by yigals on 2007-04-04
No matter what i'm typing in the terminal, it won't be saved for next restart.
examples:
mounting Windows partition
change of alias

I tried to see if it's permissions thing, but 'sudo alias' will return an error.

---

### Post by Skrynesaver on 2007-04-04
When you set things in a shell (terminal) it is set for that session only.
if you wish to make aliases available in future shells you must add them to your ~/.bashrc
eg 
```
echo "alias j='jobs'" >>~/.bashrc
```You can mount partitions automatically by adding them to your 
/etc/fstab [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm) provides guidance on this

Hope this helps

---

### Post by yigals on 2007-04-04
This explains alot 
so ~/.bashrc is running every startup?
If not how can I add commands to the startup?

---

### Post by Skrynesaver on 2007-04-04
Depends on how you define startup
~/.bashrc is run every time you start a terminal and inherited by that terminal. 
~/.bash_profile is run everytime you log in to a terminal ie. ALT-F2
everytime the computer starts init runs the daemon processes

---

