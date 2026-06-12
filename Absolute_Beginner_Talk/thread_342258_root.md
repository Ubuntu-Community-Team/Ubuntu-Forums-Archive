---
title: "root"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-01-19
How do I log in a root

I can do sudo in terminal but not on the login screen

---

### Post by jvc26 on 2007-01-19
Is there any need to log in as root? You can but its not advisable as it makes your system much more vulnerable, and isnt really needed at all as all commands can be run as sudo to sort them out if you need the root permissions.
Il

---

### Post by halitech on 2007-01-19
root is disabled so we don't do stupid things like log in as root and hose the system. 

sudo is all we need when doing things.

---

### Post by RED WIND on 2007-01-19
wut I am trying to do is get to the file system so because I am running apache on it and now I want to edit and delete files that are default but all the folder are locked is there some way I can do this from terminal?

also not related but how do you start apache in ubuntu (not the same as centos)?

---

### Post by taurus on 2007-01-19
If you need to edit something that requires root, run

```
gksudo gedit **filename**
-or-
sudo nano -w **filename**
```

---

### Post by halitech on 2007-01-19
from a terminal, type in 

```

gksudo nautilus

```

and then you can go anywhere and move/delete/open files. 

BE VERY CAREFUL in this though, it will not ask you to confirm that you want to make changes and you can hose your system.

as for restarting apache, from the terminal, type in

```

sudo /etc/init.d/apache2 restart

```

---

### Post by RED WIND on 2007-01-19
how do I delete??? and if I make something on my username and they how would I put it in root

---

### Post by jvc26 on 2007-01-19
select the file and press DEL will delete things ;)
Il

---

### Post by halitech on 2007-01-19
from within nautilus, just right click -> move to trash or sudo rm (filename) from the terminal

---

### Post by Pobega on 2007-01-19
Well the best thing to do would (In my opinion) be to set the properties of /var/www so your group (redwind, or whatever you have) has read and write access. I'm not sure one how to do this in the terminal, someone else might be able to chime in here.

**Edit:** My guess is > sudo chmod -R 660 /var/wwwbut I'm not 100% sure.

---

### Post by halitech on 2007-01-19
I think you are pretty close, I think it is  +R instead of -r

---

### Post by Pobega on 2007-01-19
> **halitech said:**
> I think you are pretty close, I think it is  +R instead of -r
Yeah, it's a capital not a lowercase; I just noticed that now. But it's a - not a +, I'm pretty sure. 

[quote=man chmod]       -R, --recursive
              change files and directories recursively[/quote]

You also may need to use chown, but I have no experience using that (I'm looking into it right now.)

**Edit:** If my first command doesn't work, you can try using this:> chown -hR <username> /var/www

---

### Post by halitech on 2007-01-19
well, between the 2 of us we got it right ;) I just double checked myself and found that it was -R and was about to come back to correct my post

---

