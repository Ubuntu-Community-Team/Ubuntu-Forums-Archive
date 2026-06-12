---
title: "Installed package, now where is it?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by HugoRune on 2007-06-12
When I install a program by package, I often have trouble finding it afterwards.

Most of the time it can be found in the application menu, but not always where I would expect it. 
Sometimes it ends up somewhere in the system menu.
Sometimes it can only be started from the command line, but the binary name is not neccessarily identical with the package name, so this is very hard to find.
Sometimes I fail to find it at all.

Is there something basic that I am missing? Is it supposed to work this way?
Is there a way to choose the place it appears in during installation?

---

### Post by Cypher on 2007-06-12
If you install a program by package, then you know the package name. So open a terminal by going to Applications->Accessories->Terminal and type
```

dpkg -l | grep <package>

```
This will tell you what the package name is exactly called when installed, you can now list the contents of that package by doing
```

dpkg -L <package>

```

The lowercase 'el' lists all packages and you are basically 'grep'ing (searching) for your package name. The uppercase 'el' will list the contents of a particular package.

---

### Post by seshomaru samma on 2007-06-12
you can use 
```
dpkg -L name_of_package 
```
to find out whereare it's files
the one you are looking for is usually in /usr/bin
if you use the command line to install (which you should) you will know where it was installed to

EDIT: the above post explains it better...............

---

