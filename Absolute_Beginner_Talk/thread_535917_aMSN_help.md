---
title: "aMSN help"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by mountin_goat on 2007-08-27
im trying to install the music plugin for aMSN, but when i try extract the plugin to the "/usr/share/amsn/plugins" folder it comes up with: Extraction not performed

You don't have the right permissions to extract archives in the folder "/usr/share/amsn/plugins"

any help please

---

### Post by Jimmyfj on 2007-08-27
You need to have root privileges in order to do things like that.

```
gksu nautilus
```

Write that code in a terminal and enter your password. Then unpack the file and move the folder to the plugin folder this way.

---

### Post by Ubuntized! on 2007-08-27
You should do it with the command line!
Do this:

1 - extract the plugin to your desktop
2 - if you are using gnome, open a terminal and type "sudo nautilus" (if u are using kde, type "sudo konqueror" instead) both kommnads are to be typed without double quotes!!
3 - navigate to /usr/share/amsn/plugins and then drop inside this folder, the folder u just extracted on ur desktop!
4 - close nautilus (or konqueror)
5 - enjoy ur plugin!

this is the easiest and noobest way but not the shortest!!

---

### Post by mountin_goat on 2007-08-27
> **Jimmyfj said:**
> You need to have root privileges in order to do things like that.

```
gksu nautilus
```

Write that code in a terminal and enter your password. Then unpack the file and move the folder to the plugin folder this way.

i did that but this happened:

nic@nic-laptop:~$ gksu nautilus
(nautilus:18375): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

