---
title: "A little help with adding to the list of Repositories"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2005-12-28
Hi guys.

I have been following a decent tutorial/guide on ubuntu, and am familiarising myself with linux in general (something I havent done despite doing an MSc in Computing!!!) Anyway...

I'm trying to right click on the sources.list and want to select 'scripts' then open as root. My problem is that there isn't an option for me to do this? I want to do this so that I can add the universe packages, but I want to just be able to edit this in general if required (I cant do this if I open it up by double clicking)

Can someone help with this problem?

Thanks
Andrew

---

### Post by Lord Illidan on 2005-12-28
Most people like doing it via the terminal...

```
sudo gedit /etc/apt/sources.list
```

---

### Post by xtacocorex on 2005-12-28
This is probably easiest to do from the command line with:
if you know vi
```

sudo vi /etc/apt/sources.list

```
or if you use KDE
```

kdesu kate /etc/apt/sources.list

```
or if you use Gnome
```

gksudo gedit /etc/apt/sources.list

```

An updated sources.list can be found here: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

