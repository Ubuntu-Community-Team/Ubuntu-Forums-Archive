---
title: "How do I access the root user?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by decay85 on 2006-10-03
When I set up Ubuntu on this computer I never typed in a password for a root user. I was only given the option to make an administrator account. What did I do wrong?

---

### Post by bulldog on 2006-10-03
When you need root rights you use sudo.

Then put your password and you have the rights for about 15 minutes.

If you need to be root for a longer periode you kan use sudo -s

---

### Post by deadgobby on 2006-10-03
That is simple and easy to do.
Open up your new friend Terminal that can be found at 
Applications>Accessories>Terminal
And ether type it in or the copy and past method.

sudo passwd root

Gobby

---

### Post by aysiu on 2006-10-03
There's no need to enable root.

If you want to have a terminal command be executed with root privileges, you preface the command with *sudo*: ```
sudo aptitude update && sudo aptitude install xnest
```

If you want to have a string of commands run with root privileges and don't want to type *sudo* in five times, just do ```
sudo -i
``` and this will give you a root terminal.

If you want to make graphical (drag-and-drop) changes as root, press Alt-F2 to get a run dialogue (or create a keyboard shortcut or launcher for one of these commands): 

Ubuntu ```
gksudo nautilus
``` Kubuntu ```
kdesu konqueror
``` Xubuntu ```
gksudo thunar
```

---

