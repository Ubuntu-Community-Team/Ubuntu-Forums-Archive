---
title: "sources.list read only?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Esca on 2005-12-14
Hi,

First off all i am a total linux noob so don't blame me for asking idiotic questions :) .
I have googled for this issue (wich might be verry simple) and browsed several forums...

I found plenty of info on editing the sources.list but when i try to do so i don't seem to have the rights, the rights are for the root user and i get read only... :confused: 

What to do? 

thanks 

edit: taking a closer look i can't do anything on my the partition that contains the os, only in my "personal folder" seems to be accessible

Frederic

---

### Post by Perfect Storm on 2005-12-14
You need to write sudo before thte command like:
```

sudo gedit  /etc/apt/sources.list

```

sudo let you make adminstration tasks.

---

### Post by mcduck on 2005-12-14
you should use 'sudo' command to do things with root privileges. Try running 'sudo gedit /etc/apt/sources.list' in terminal.

edit: too slow :D

---

### Post by Esca on 2005-12-14
thank you for you're help

problem fixed

---

### Post by thezerogroup on 2005-12-14
You can also use the command line editor VI 
```
sudo vi  /etc/apt/sources.list
```

---

### Post by mcduck on 2005-12-14
you can also use 'gksudo nautilus' to open a file manager window as root.

If you need it often, you can make a laucher in your panel with that command. Right-click the panel, select 'add to panel' and then 'custom application launcher'. Then enter that command in 'command'-field, give your launcher a name and choose whatever icon you wish to use..

---

### Post by carlosqueso on 2005-12-14
you have two ways that you can do that:

```
gksudo nautilus
``` will give you nautilus that runs as root.  If you want to make a directory somewhere in which you aren't allowed, navigate there in a console and type ```
sudo mkdir <foldername>
```  However, why are you creating directories in the filesystem? Is it something we can help with?

EDIT: 3rd!?! Dang I'm slow

---

