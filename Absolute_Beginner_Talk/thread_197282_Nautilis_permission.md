---
title: "Nautilis permission"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Wetscoast Gus on 2006-06-15
I can't figure out how to move files in nautilis, as every time I try to do so, I'm told I don't have permission. I can't find any option in the preferences to ask for the root password, either.

---

### Post by jrattner on 2006-06-15
[QUOTE=Wetscoast Gus]I can't figure out how to move files in nautilis, as every time I try to do so, I'm told I don't have permission. I can't find any option in the preferences to ask for the root password, either.[/QUOTE]

If your moving files that require root access why not open nautilus as root:

```
sudo nautilus
```

or consider using the command line, its faster and more effiecent:

```
sudo mv file destination
```

If your working with directories consider using the -f and -r flags with mv.

Consult 'man mv' for more information

---

### Post by anaconda on 2006-06-15
try 

sudo nautilus

in terminal

---

### Post by aysiu on 2006-06-15
[QUOTE=anaconda]try 

sudo nautilus

in terminal[/QUOTE] *sudo nautilus* will work, but technically you're supposed to use *gksudo*, not *sudo*, for graphical applications.

The proper way to do it: press Alt-F2 and type ```
gksudo nautilus
```

---

### Post by anaconda on 2006-06-15
hmmm.. interesting.

Why gksudo instead of sudo? could you explain, or give a link?

---

### Post by bruce89 on 2006-06-15
[QUOTE=anaconda]
Why gksudo instead of sudo? could you explain, or give a link?[/QUOTE]
It's graphical, not sure why that helps, except to make it look prettier.
What does gksu do, is it the equivalent of su?

---

### Post by aysiu on 2006-06-15
There are three reasons to use *kdesu* or *gksudo* for graphical applications, as opposed to using *sudo*:

1. In certain applications, if you launch them with *sudo*, your permissions will become corrupted. One of the hidden folders in your /home directory will become owned by root or your .ICEauthority file might adopt the wrong permissions, which will bar you from logging in to your user account. This is rare, but it does happen.

2. Certain applications simply do not work with *sudo*. For example, try ```
sudo kate
``` and see what happens.

3. You cannot create a launcher or keyboard shortcut for the command (i.e., you must use the terminal), as *sudo command* will prompt you for a password in the terminal only. *gksudo command* and *kdesu command* will pop up a graphical password prompt.

Please spread the word, so I won't have to keep explaining this every time.

Yes, there are some cases where *sudo command* will work for a graphical application, but it's a good idea to form proper and consistent habits of using *sudo* for terminal applications and *gksudo* or *kdesu* for graphical applications.

---

