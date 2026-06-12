---
title: "How to list packages in shell"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-10-30
Hey is there anyway to list the same list that synaptics show, but in the bash? Cause I removed 1 or 2 important packages and I dont have more GUI lol :)

So thats it, I only want to list to remember the correct name of the package

Thanks,
Krebs

---

### Post by Denn1s on 2007-10-30
try:
```

apt-cache pkgnames

```

or you can use aptitude:

```

sudo aptitude

```

wich has a nice interface

---

### Post by kevdog on 2007-10-30
sudo apt-cache search <put something that sounds like package name here>

This command above will bring up packages from repositories that are similar to what you typed

sudo aptitude search <package name>

You need to get the package name spelling correct on this one, but I think this command will tell you if you already have the package installed.

---

