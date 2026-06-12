---
title: "installing GIMP"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by captain creative on 2006-09-24
hi, I am completely new to LINUX and UBUNTU, I am confused about how to install or what i need to install in order to run The GIMP.Having checked out the GIMP homepage apparently I need to download various bits and pieces to configure it myself ??? It also states that there are various sites that have download 'packages' available already compiled and ready to use?? anyone got any clues?

Thanks for your help

captain creative.

---

### Post by xpod on 2006-09-24
You can just go into "System\administation\synapyic package manager" and you should find gimp in there.
It will also get the extra bits` and bob`s it needs once you just check the box for gimp.

You might need to go into "settings" in synaptic then "repositries" and click the "add" button then check the extra boxes to enable the extra repo`s.

It should also be available in "add\remove"...OR if you wanted to use the terminal...ooooooo
Then you would go to "applications\accesories\terminal" and then type
```
sudo aptitude update
```
 and 
```
sudo aptitude install gimp
```

This will also install all dependancies AND remove them if you decide you want rid of the gimp

GOODE LUCK..If im wrong someone will point out the errors of my ways:D

EDIT: aint you already got gimp if your using Ubunto??...APPS\GRAPHICS????

---

### Post by steve.horsley on 2006-09-24
But the GIMP is always installed by default. Look under Applications->Graphics, I think. Or try the command **gimp** in a console. It it's not there for some strange reason, use Synaptic like xpod says. Downloading bits and pieces from their web site is for masochists and the terminally curious.

---

### Post by wydra on 2007-11-19
Yeah, but the latest version, GIMP 2.4.1 isn't on there, and it's stable according to the site...

---

