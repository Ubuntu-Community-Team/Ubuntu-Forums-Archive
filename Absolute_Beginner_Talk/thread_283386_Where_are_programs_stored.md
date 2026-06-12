---
title: "Where are programs stored?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-24
Where are programs stored on the Filesystem?

When I remove a program, I want to delete all traces of the program to make it look like it never existed. Even if you remove a program, some still leave some files. Thanks!

---

### Post by xyz on 2006-10-24
Hi,
For starters, try in a terminal:
```
locate k3b
or
which k3b
```
I'm using k3b as an example.
Another simple way is to open Synaptic and search/right click on,say, k3b + on Installed Files.
This is not very academical but not too bad for a start.

---

### Post by Bachstelze on 2006-10-24
Synaptic has a "Completely remove" option. You can also use the --purge switch when running apt-get remove.

---

### Post by zappa on 2006-10-24
sudo aptitude purge program (or synaptic way) removes it completely except maybe some prefs in your home folder. You can safely delete these by hand.

---

### Post by xyz on 2006-10-24
A good HowTo to clean things up:
[ Cleaning up all those unnecessary junk files by WackToMac]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=unnecessary+files")
Also using the command line:
```
sudo aptitude (instead of sudo apt-get)install your_program
```
should remove it (dependencies) much better.
In the link I gave you, you'll also be able to learn how to create a sort of filter (called "Orphaned" if you wish it to be named so)...just read about it and report back.
Good luck.

---

