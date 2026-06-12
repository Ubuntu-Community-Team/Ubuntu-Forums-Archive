---
title: "Padlock Icon on folder, can't delete folder ???"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ChenJianYi on 2007-05-21
hi, i have a problem. I can not delete folder from the extracted tar.gz file
The folder has a padlock icon. I have seen the properties and it's not read-only.
How can i delete this folder ?

Thank You.

---

### Post by justleen on 2007-05-21
try removing it as root.
press ctrl-f2 and type ```
gksudo nautilus 
```
enter your password, browse to the folder, and try deleting it again.

---

### Post by starcraft.man on 2007-05-21
> **justleen said:**
> try removing it as root.
press **alt**-f2 and type ```
gksudo nautilus 
```
enter your password, browse to the folder, and try deleting it again.

That would be alt I believe you were referring to. A handy shortcut for all to remember though, easy way to pop things open. Otherwise, nothing wrong with the solution. I

Have a nice day :).

---

### Post by Spam Banjo on 2007-07-18
> **justleen said:**
> try removing it as root.
press ctrl-f2 and type ```
gksudo nautilus 
```
enter your password, browse to the folder, and try deleting it again.

Great tip!!! Fixed My Problem!

---

### Post by The Seeker on 2007-07-18
Edit: Spotted Alt correction above. Damn this cursed (albeit self-inflicted) hangover.

---

### Post by Paul86fxr on 2008-01-11
Worked fine, thanks. I'm new like everyone else and making plenty of mistakes as I learn, having a blast too!

---

### Post by stchman on 2008-01-11
> **ChenJianYi said:**
> hi, i have a problem. I can not delete folder from the extracted tar.gz file
The folder has a padlock icon. I have seen the properties and it's not read-only.
How can i delete this folder ?

Thank You.

I know we are not supposed to talk about this on the forum but it seems to be appropriate here.  Type the following in a terminal.

```
sudo rm -rf <folder you wish to delete>
```

Remember, the rm command is very powerful and MAKE SURE that you really want to delete that folder as you will not be able to get it back.

---

