---
title: "run as root"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by ButchSpeer on 2008-01-10
I installed Adept Manager but it wants to be run as root. Could anyone show me the command. I've read a lot of tutorials but I guess I'm not very bright this evening. thanks for any & all help.

---

### Post by wolfen69 on 2008-01-10
if you're wondering how to become root in terminal, sudo -i  will do it.

---

### Post by dgray_from_dc on 2008-01-10
Normally, when you run adept from the menu, you'll get a dialog box asking you for a root password.  Is that what you mean?  Linux will not let you install packages without root privileges.  If you're trying to run it directly from the command line, use

```
sudo adept
```

You'll then be prompted for your password.

If you're not being asked for a password when starting from the menu, there may be a problem with communication to kdesu (if you're in KDE) or gksu (if you're in Gnome).

Although I use KDE, my personal preference is the synaptic package manger.  It's a lot more speed efficient when it comes to filtering and searching for specific packages especially on older CPUs.

---

### Post by barbedsaber on 2008-01-10
I think you can log in as root, by typing root as your username, and then the password you chose when you set up your computer, HOWEVER this is genrally a BAD thing, and you should only do it when you ABSOULOUTLY MUST! just take my word for it. 

EDIT: I waswrong about being able to log in as root, but you should still be wary of root, with great power, comes great responsibility.

---

### Post by mikewhatever on 2008-01-10
Try <gksudo adept> instead of simply sudo.

---

