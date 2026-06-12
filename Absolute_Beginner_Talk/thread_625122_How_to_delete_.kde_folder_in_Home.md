---
title: "How to delete .kde folder in Home?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by fifth_rune on 2007-11-27
It's taking up a lot of space and I don't even use KDE (pure Gnome).  How do I get rid of this thing and make sure it doesn't come back?

---

### Post by Dr Small on 2007-11-27
Have you tried?
```
rm -r /home/`whoami`/.kde/
```

---

### Post by fifth_rune on 2007-11-27
It's not that I haven't considered, I just don't want to damage my system.  Basically I want to know if it's ok to delete the folder.

---

### Post by Dr Small on 2007-11-27
Well, if you have not removed KDE from the system yet, then you could add "--purge" to the remove command, and it would remove all of the kde conifiguration files.

---

### Post by dasunst3r on 2007-11-27
*.kde* contains user preferences and data relating to KDE.  If you are sure you are using absolutely no programs from KDE (AmaroK, Kopete, K3b), then it's safe to delete.  At worst, the folder will regenerate and you will start off with the default preferences when you do launch one of the programs.

---

### Post by talktechnow on 2007-11-27
Why not move the .kde folder to .kde.old and then test it like that, assuming it works 100% delete it.

Thats how I would go about it.

---

