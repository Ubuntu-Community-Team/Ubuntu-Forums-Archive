---
title: "[SOLVED] Ubuntu Server command line"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jamesrfla on 2007-10-27
Is Ubuntu Server edition all command line? If it is then how do you add folders to share. I have already changed the password in samba. What do I do next?

---

### Post by taurus on 2007-10-27
Server = commandline

You create new directory with the mkdir command.

```
sudo mkdir **directory_name**
```

---

### Post by jamesrfla on 2007-10-27
So Ubuntu Server is all command line? I tried that taurus and nothing happened. Any other ideas? Also how do you change the workgroup?

---

### Post by taurus on 2007-10-27
What exactly did you type on a prompt?  What directory do you want to create?

p.s.  If you want some kind of window manager to make your life easier, then you have to install Gnome (or KDE).

---

### Post by funrider on 2007-10-27
yes, you should try the regular ubuntu and get yourself familiar with the command line first.

---

### Post by jamesrfla on 2007-10-27
I use Ubuntu Desktop for my file server. I just wanted to try Ubuntu Server. I thought it was just like Ubuntu Desktop except with all of the programs. I am just going to stay with the desktop edition. I typed sudo mkdir directory_james.

---

### Post by taurus on 2007-10-27
And you don't see a new directory called **directory_james**?

```
ls -la
```

---

### Post by jamesrfla on 2007-10-27
I think it is in root. When I looked to the left it said root. I am going back to Ubuntu desktop. Thanks for the help.

---

