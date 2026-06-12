---
title: "Owner permission issues. Help?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2006-11-17
Right! So, I'm a really, really new Ubuntu user. Never knew anything about Linux prior to about a week ago. I'm currently running the Hoary Hedgehog version, because my external CD burner isn't working and I have to wait for my Dapper CDs to come in by snail mail.

Anyway, my question is: **how do I get myself owner permissions on Ubuntu**? For some reason, I only have user permissions, which means that every time I try to install something like GCC (which I *really* need at moment, because I need to install something to unzip my .rars), I can't, because I'm not allowed to create new directories in /usr. I've looked all over the system and can't find anything that will help me change my permissions.

Also, should I expect this problem when I get Dapper, too, or is this just a one-time thing? (Hoary is also missing a bunch of plugins that I can't install because, again, no owner permissions).

---

### Post by taurus on 2006-11-17
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude install build-essential
```
And if you need to install something to your system, use the sudo command.  No need to log in as root and when it asks you for the password, use the same one that you log in...

---

### Post by echo $USER on 2006-11-17
> **Halfling Rogue said:**
> Right! So, I'm a really, really new Ubuntu user. Never knew anything about Linux prior to about a week ago. I'm currently running the Hoary Hedgehog version, because my external CD burner isn't working and I have to wait for my Dapper CDs to come in by snail mail.

Anyway, my question is: **how do I get myself owner permissions on Ubuntu**? For some reason, I only have user permissions, which means that every time I try to install something like GCC (which I *really* need at moment, because I need to install something to unzip my .rars), I can't, because I'm not allowed to create new directories in /usr. I've looked all over the system and can't find anything that will help me change my permissions.

Also, should I expect this problem when I get Dapper, too, or is this just a one-time thing? (Hoary is also missing a bunch of plugins that I can't install because, again, no owner permissions).

To install programs or make system changes you need root privialges (sudo)...

So to install gcc, copy and paste this into the terminal...

> sudo apt-get install gcc

---

### Post by jimbren on 2006-11-17
What you're looking for are root or administrative rights.  If you're working form the command line to install something, you'll want to start your line wit *sudo*, and then enter **your password** when prompted to.

Say you want to install gaim from the command line...

```
sudo apt-get install gaim
```

Does that make sense?

jimbo

---

### Post by Halfling Rogue on 2006-11-17
Ohhh. Thanks very much, all of you! Hopefully my installations will cooperate now. *goes to give File Roller another shot*

---

### Post by CatKiller on 2006-11-17
To be able to open .rar files, you'll need to install the **rar** package from the repositories.
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[http://ubuntuguide.org/wiki/Ubuntu#Repositories](http://ubuntuguide.org/wiki/Ubuntu#Repositories)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

To run administrative things from the command line, you'll need to use **sudo**, as you've already been told. The standard pages you should read on the subject are these:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

To compile things, you should install the **build-essential** package, as taurus says. It should be on the cd.

You might also want to read these pages:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Welcome to the community.

---

