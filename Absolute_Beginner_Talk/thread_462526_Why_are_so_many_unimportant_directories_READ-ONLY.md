---
title: "Why are so many unimportant directories READ-ONLY?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by wie6Ein0 on 2007-06-02
Why are there so many unimportant directories READ-ONLY? For example, the wallpaper folder, themes folder, etc.

I think that by default, the users should have full READ/WRITE privileges to those directories -- especially the wallpaper folder.

---

### Post by taurus on 2007-06-02
Everything in /usr is read-only for users and only root can write to them.  And if you need to move some wallpappers, icons, themes, etc. to /usr/share, then use

```
gksudo nautilus
```

---

### Post by Maxster on 2007-06-02
agreed- why is this?

---

### Post by wie6Ein0 on 2007-06-02
> **taurus said:**
> Everything in /usr is read-only for users and only root can write to them.  And if you need to move some wallpappers, icons, themes, etc. to /usr/share, then use

```
gksudo nautilus
```

Okay, understood. I have used *[COLOR="YellowGreen"]sudo nautilus[/COLOR]* before to move wallpapers. What is the major difference using *[COLOR="YellowGreen"]gksudo[/COLOR]* instead of *[COLOR="YellowGreen"]sudo[/COLOR]* with nautilus?

---

### Post by taurus on 2007-06-02
> **westoncampbell said:**
> Okay, understood. I have used *[COLOR="YellowGreen"]sudo nautilus[/COLOR]* before to move wallpapers. What is the major difference using *[COLOR="YellowGreen"]gksudo[/COLOR]* instead of *[COLOR="YellowGreen"]sudo[/COLOR]* with nautilus?

_Please_ use

```
gksudo nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2007-06-02
Who says they're unimportant?

By the way, for the difference between *sudo* and *gksudo*, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by wie6Ein0 on 2007-06-02
> **aysiu said:**
> Who says they're unimportant?

Me. You're right though -- they're not unimportant, just not as important as the other directories...

---

### Post by H.E. Pennypacker on 2007-06-02
> **aysiu said:**
> Who says they're unimportant?



Who says they're important?  It doesn't make sense to lock everything that is not in a person's home folder.  

As long as a cracker (a person seeking to damage your computer) can't make malicious use of, say a wallpaper folder, what's the big deal?  Sure, the cracker can get rid of your wallpapers, or whatever, but the same could be said for the home folder.  I keep lots of important images in my home folder, but it is still not "locked."

---

### Post by aysiu on 2007-06-02
> **H.E. Pennypacker said:**
> Who says they're important?  It doesn't make sense to lock everything that is not in a person's home folder.  

As long as a cracker (a person seeking to damage your computer) can't make malicious use of, say a wallpaper folder, what's the big deal?  Sure, the cracker can get rid of your wallpapers, or whatever, but the same could be said for the home folder.  I keep lots of important images in my home folder, but it is still not "locked."
Well those folders contain files that are supposed to be available system-wide for all users. Of course, if you're the only user on your computer, those files may not seem important to you, but if you happen to delete all the icon themes, then new user Jane may be a little upset when she logs in and has no icons...

The /home/*username* directory files affect only *username*, so no matter how "important" or "not important" they are, they can be modified by *username*. The /usr/ directory can be modified by only an administrator, since that directory affects *all* users. If you're the only user on the computer, then you have administrative privileges and can delete from the /usr directory with the help of *gksudo*.

---

