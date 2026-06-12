---
title: "List of programs"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-12-17
is there a way to see all of the programs/utilities installed on your system, I mean better then synaptic and add/remove.  It doesn't even have all of the programs.  And also if it can show the path and size.

---

### Post by Thanoulis on 2007-12-17
Not of one that i'm aware of...:)
But if you'd like to see all the executable ones, try listing your /bin and /usr/bin directories...

---

### Post by sports fan Matt on 2007-12-17
Can i ask how you think Symnaptic doesnt have all the programs listed?  It seems to under "all available applications" in whatever desktop you are using (XFCE, GNOME, KDE, PUPPY, etc)

It always has them all listed for me..

---

### Post by drs305 on 2007-12-17
This command will create a text file with all the installed packages called installed-pkgs and put it on your desktop:

```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```

Added later:
This command will give you a simple text file that lists the main package name and it's status (install, deinstall, etc). It doesn't give version numbers or any specific information, as lucia_engel notes below. It is most often used to make an installed programs list for use with another computer in order to download the same packages with the --set-selections option.

---

### Post by lucia_engel on 2007-12-17
> **sox fan Matt said:**
> Can i ask how you think Symnaptic doesnt have all the programs listed?  It seems to under "all available applications" in whatever desktop you are using (XFCE, GNOME, KDE, PUPPY, etc)

It always has them all listed for me..

Not only that, size and path of all the installed files are listed as well in Synaptic, unlike the dpkg command.

---

### Post by sports fan Matt on 2007-12-17
Engel, Agreed,

Dont forget the repos as well:)

---

