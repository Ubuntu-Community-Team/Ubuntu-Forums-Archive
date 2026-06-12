---
title: "[SOLVED] Root versus Regular user"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by drbk563 on 2008-04-13
Is it better to running Ubuntu in root mode or using another username?

Thank You

---

### Post by j.bunce on 2008-04-13
Never ever run your system as root. It's a huge security risk. If you need to perform an administrative task, in a terminal such as gnome-terminal or xterm, use the command
```
sudo
```

Is there any particular task that you're trying to perform, or is this just a general question?

---

### Post by tamoneya on 2008-04-13
you always want to run ubuntu or linux in general as a different non-root user.  Root user can modify any file and this is a large security risk.  What you do instead is you call "sudo" when you need root privileges but other than that you run ubuntu as non-root.

---

### Post by ibutho on 2008-04-13
Running as root is generally discouraged for security reasons and to protect the system. You should generally use your normal user account. If you need to do any sysadmin tasks, just use sudo and gksudo to execute commands with root privileges or run gui apps with root privileges.

---

### Post by diablo75 on 2008-04-13
You cannot actually login as root by default.  What you can do is temporarily usurp root user level privileges using sudo in a terminal window (just as an example).

It is better to NOT run as root.  The biggest reason for this is that it will help prevent you or possible  from accidentally doing something that will cause harm to the system.

---

### Post by aysiu on 2008-04-13
> **drbk563 said:**
> Is it better to running Ubuntu in root mode or using another username?

Thank You
Those aren't the only two options. The best thing to do is to run it as default - an administrative user who is a limited user most of the time but is able to temporarily assume root privileges for certain tasks with password authentication.

Read more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In other words, just use Ubuntu as packaged, unless you know what you're doing (i.e., don't have to ask people on the forums how to do otherwise).

---

### Post by drbk563 on 2008-04-13
For example when I am installing programs such as Java or any other applications like Real Player. Should I be installing these software under root or another username?

Thank You

---

### Post by tamoneya on 2008-04-13
you should install them under a different user name who is in the admin group.  This means that you can call sudo in order to get the root privileges required to install java.

---

### Post by drbk563 on 2008-04-13
Thank you all for all your help. Everything now makes sense now.

---

