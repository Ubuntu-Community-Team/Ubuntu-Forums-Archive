---
title: "I need to log in as root, is that possible?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by peterv6 on 2007-10-06
I'm new to Ubuntu, so please bear with me.  I have administration tasks I want to perform as root.  I don't want to use sudo for these tasks, I want to log in with the root account.  I enabled the root account, but if I restart and attempt to login as root, it tells me root logins are not allowed.  Is there a way to get around this?  Also, I need to use the Synaptic utility, but I can't find it anywhere.  I looked under system, but there is no administrative icon anywhere.  Please help!

---

### Post by taurus on 2007-10-06
What kind of tasks do you need to run as root?  You can log in as root if you have created a password for it first.

```
sudo passwd root
sudo -
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nest on 2007-10-06
i dont know if there is a way to log into gnome/kde as a root. i just use sudo.

and you can use synaptic simple doing:

**sudo synaptic** in the terminal.

---

### Post by peterv6 on 2007-10-06
The problem I'm having is that there is no system administration icon anywhere.  In the help section, it says to go to system, administration.  I'm using KDE.  Any ideas on why it's missing?

---

### Post by Tyke91 on 2007-10-06
logging in as root will not make a system administration icon pop up magically... in gnome it is indeed under system>administration, but in kde i think the administrative tasks are spread out in menus such as "System" and "Utilities"

---

### Post by cyful on 2007-10-06
Very possible, 

1. Goto user setting and give root a password
2. go to login setting, under security, allow administrator to login

DONE

---

### Post by bodhi.zazen on 2007-10-06
You do not *need* to set a password or directly log in as root.

FYI : If you set a password for root, and want to disable the root account 

```
sudo passwd root -l
```

You can do most everything with sudo and gksu

Open a terminal and use sudo for single commands.

If you want to change to root, use ```
sudo -i
```

If you want to run graphical applications as root, start them with gksu, like this : ```
gksu nautilus
```.

What else do you need ?

---

