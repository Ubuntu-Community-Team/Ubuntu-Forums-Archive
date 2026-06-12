---
title: "Trying KDE on Ubuntu"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by morwyn on 2006-03-23
I am new to Linux and I've just started trying Ubuntu, but I'm interested in checking out KDE as well, so I was thinking about adding kde. What are the advantages/disadvantages versus installing Kubuntu? I'm not really sure what to do...

---

### Post by bluevoodoo1 on 2006-03-23
```
sudo apt-get install kubuntu-desktop
```

Will get it for you. I believe it's about 900MB of data? So it will take a bit of time to download.

You will have all of the KDE applications as well as your GNOME apps in your menus. Might be considered annoying, but you can uninstall what you don't like or don't use. (There's a thread on how to uninstall all of the kubuntu-desktop if later you don't like it). 
Just experiment. I found that KDE's K3b is an excellent burning program and Konqueror is neat too.

---

### Post by Stealth on 2006-03-23
Yea, you can always do a: sudo apt-get install kubuntu-desktop

and have the best of both worlds! :mrgreen: 

Of course, if you just want certain KDE apps (Amarok and K3b) you CAN install them separetly too...

---

### Post by Adrian on 2006-03-23
[QUOTE=morwyn]I am new to Linux and I've just started trying Ubuntu, but I'm interested in checking out KDE as well, so I was thinking about adding kde. What are the advantages/disadvantages versus installing Kubuntu? I'm not really sure what to do...[/QUOTE]

One of the disadvantages of installing the **kubuntu-desktop** package is that it is difficult to remove if you don't like it. One solution is to use **aptitude** instead of **apt-get** when you install the package. The syntax is the same, so you install it by doing a:
```

sudo aptitude install kubuntu-desktop

```
This way it can easily be removed again by typing:
```

sudo aptitude remove kubuntu-desktop

```

Also, if you don't want the KDE programs to appear in your GNOME menus (and vice versa), check out these threads for the solution:
[http://www.ubuntuforums.org/showthread.php?t=123969](http://www.ubuntuforums.org/showthread.php?t=123969)
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

However, a separate Kubuntu partition will give you a cleaner system, so many people prefer to keep them separated.

---

