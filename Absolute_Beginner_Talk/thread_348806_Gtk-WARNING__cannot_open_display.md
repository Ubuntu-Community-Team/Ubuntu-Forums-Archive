---
title: "Gtk-WARNING **: cannot open display:"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by fleet on 2007-01-29
Get "Gtk-WARNING **: cannot open display:" when trying to open an application from the terminal as the root user. I can open applications from the terminal as a normal user but not as root.

---

### Post by taurus on 2007-01-29
Please use the gksudo to open a GUI app as root.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by fleet on 2007-01-29
Yes, that- and most variations of it- is the command I have been trying. Same error regardless

---

### Post by taurus on 2007-01-29
Can you provide the exact command that you tried to run?

What happens if you run this command from a terminal, logging in as a regular user?

```
gksudo synaptic
```

---

### Post by fleet on 2007-01-29
If I run the command "gksudo synaptic" from the terminal as a user the application starts straight up with oddly no prompt for the root password. If I try similar as root then I get '(gksudo:10665): Gtk-WARNING **: cannot open display'. Thanks for trying to help.....

---

### Post by taurus on 2007-01-29
Is there any reason you need to log in as root instead of using sudo/gksudo?  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2007-01-29
You cannot run GUI apps from a root shell. If you want to run a GUI app as root, use gksudo from a user shell.

---

### Post by fleet on 2007-01-29
Yes. That actually makes sense. Thanks I was trying to use nautilus as root in order to avoid having to learn the shell commands. Having looked at a few sites I think I will go ahead and do my file management from the Terminal. I always liked DOS so I should find my way. Thanks for your help. Rgds:D

---

### Post by Confused_MindCrawler on 2007-03-02
Hi, I am an absolute newbie. My problem is as follows;
I have Dapper Drake and cannot start firefox. I get the message : "Gtk-Warning **: cannot open display:

I have tried as root or as user, but I get the same results. I have also tried gksudo firefox  (as user not root) with the same results. Also tried xhost +LOCAL but still the same.
Can you help?

---

