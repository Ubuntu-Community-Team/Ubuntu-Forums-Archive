---
title: "A really silly question"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ataiger on 2007-07-02
Hi, I installed Feisty 2 days ago and have a question.

Whenever I choose a program to install and install them, they often install another packages needed for them.

What I am curious about is.... if I install that many other required packages, wouldn't my harddisk lack space some day? When I uninstall program packages that I intended to install for my need, the 'required packages' are not uninstalled, right? So I wouldn't be able to find what packages I don't need, and someday, there will be no space for other packages.

This might sound silly, but I'm so curious. ;)

---

### Post by Surkow on 2007-07-02
All unneeded packes will be removed if you type the following in the command line:

```
sudo apt-get autoremove
```

---

### Post by oilchangeguy on 2007-07-02
this of course depends on the size of your hard drive. and how many packages you want to install.

---

### Post by cmnorton on 2007-07-02
Your question doesn't appear silly. It sounds like you are worried about losing disk space. I understood your question as If you think Package A is going to require a certain amount of disk space, but Package A requires installation of Packages B and C, how can you plan for that. Probably, you'll have to overcompensate for drive space just to be safe.

I've had to install a second larger hard disk, and then move something large on the first disk, like /home, to that new drive. It was easy to do in Linux.However, you will probably move to a new computer before you run out of space, unless you are just installing everything you can think of. All that was because of unplanned application use and need for backup space, not because of installed packages.

---

