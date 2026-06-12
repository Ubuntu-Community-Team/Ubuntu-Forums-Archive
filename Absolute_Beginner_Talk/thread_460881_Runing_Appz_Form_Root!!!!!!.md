---
title: "Runing Appz Form Root!!!!!!"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-06-01
Hello to everyone:)

I am wondering how can I run setup application from Cd in root (from terminal) ????

Thnx

---

### Post by mlentink on 2007-06-01
I don't think I understand what you mean. What is it that you'd like to achieve? Which "setup application" on which cd do you want to use?

---

### Post by Urko on 2007-06-01
i want to install game from my cd but problem is that I must install it from root and I don+t know wich command to use to acces to cd from root in terminal :(

---

### Post by Outrunner on 2007-06-01
To get to the CD

```
cd /media/cdrom0
```

to run a file from the current directory
```

sudo <command>
```

Is this game a windows game? If so, you'll need to use wine.

---

### Post by mlentink on 2007-06-01
Is this a linux game you're installing? If yes, you should precede the command that installs it with "sudo" to install it as root. If not, you could try wine, but success is not guaranteed.

---

### Post by gerscht on 2007-06-01
You can also open a root terminal (USE WITH CARE!!!) with:
open 'normal' terminal,
```

sudo su

```
Password

You'll be root on this terminal window until you close it.

---

