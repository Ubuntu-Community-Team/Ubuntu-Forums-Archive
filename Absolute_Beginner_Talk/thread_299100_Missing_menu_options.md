---
title: "Missing menu options?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-11-13
I read on the following site:
[10 Things that make Ubuntu a Neophyte's Distribution]("http://linuxhelp.blogspot.com/2005/11/10-things-that-make-ubuntu-neophytes.html")

About a whole lot of menu options, which I can't see. Is it because I am not logged in as root? Or do I need to install some packages? What am I missing?

---

### Post by bulldog on 2006-11-13
Yes tell us......what are you missing??

---

### Post by Jagot on 2006-11-13
The article refers to an old version of Ubuntu, so some of the items are in different places or have changed.  For example, the first part about network tools can now be found in System -> Administration -> Network Tools.

---

### Post by uriahs on 2006-11-13
> **Jagot said:**
> The article refers to an old version of Ubuntu, so some of the items are in different places or have changed.  For example, the first p[art about network tools can now be found in System -> Administration -> Network Tools.

> **bulldog said:**
> Yes tell us......what are you missing??

Oh, yes. I am using Ubuntu 6.10, the main menu option i really could have done with is... Applications -> System Tools -> GParted

Is this now System -> Administration -> GParted?

---

### Post by Gerard Barberi on 2006-11-13
Try looking at the menu layout under system --> preferences.  Are the items you're looking for checked off?  If not, they won't appear in the menu.

If their not even listed and you're sure they are installed, you can run them from the terminal.

Or make an entry for them in /usr/share/applications/

You'd make a "name of application".desktop

---

### Post by Jagot on 2006-11-13
I don't think GParted is installed by default, but I could be wrong.  If not, you will need to do so:

```
sudo aptitude update && sudo aptitude install gparted
```

Either way, you should then find it under System -> Administration -> GNOME Partition Editor.

---

### Post by d3v1ant_0n3 on 2006-11-13
I only just discovered the Ubuntu Device Database (it took some hunting down too!)

It would be great if this could be run upon first boot for new users- would give an idea of how well Ubuntu preconfigures devices, and the potential problems that people will have to overcome.

---

