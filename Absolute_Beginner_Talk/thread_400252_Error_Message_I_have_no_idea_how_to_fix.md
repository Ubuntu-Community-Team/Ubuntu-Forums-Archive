---
title: "Error Message I have no idea how to fix"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by DrBeaverhausen on 2007-04-03
The message reads "A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E:Type 'OK' is not known on line 34 in source list /etc/apt/sources.list, E:The list of sources could not be read.)'

I ran the package manager and got the same error message with "Go to the repository dialog to correct the problem" added.  I'm a total noob and have no idea what all this means.:confused:

---

### Post by taurus on 2007-04-03
There is something with line 34 in your /etc/apt/sources.list!  So, you can either post it here

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
or edit it

```
gksudo gedit /apt/sources.list
```
and place a # in front of line 34 to comment it out.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

