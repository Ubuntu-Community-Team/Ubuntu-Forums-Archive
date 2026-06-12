---
title: "Running/Executing a Program/Application..?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by jandjfrench on 2007-10-15
Hi, (using Feisty and new to any Linux)

I downloaded/installed or whatever it's called "Adept"
It's on the menu "Applications/System Tools/Adept Manager"
When I click on it I get this message:

"You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions"

What do I do?  General information would be most helpful.  A search of the file system could not locate Adept and searches for information of how to run programs other than by clicking on them on the menu have not been productive.  

I've been hesitant to ask as I always seem to get these passive/aggressive responses implying  that I'm either stupid or lazy or I would have found the answer myself.  Please, none of those. Thank you.

Jim French

---

### Post by nest on 2007-10-15
go to a terminal and do this:

```
sudo adept_manager
```

sudo means Super User DO, that is the command that you will have to use when you have to use root (admin) privileges.

---

### Post by obesus_puer on 2007-10-15
A little googling and I think the command you want is```
gksu adept_manager
```
not 100% sure though since I'm still a noob.

---

### Post by por100pre1 on 2007-10-15
The command should be:

```
kdesu adept_manager
```

However, if you are only using GNOME use this:

```
gksudo adept_manager
```

---

