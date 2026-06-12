---
title: "Find and Remove Files"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-07
I don't know how to remove files with a command that automatically searches for the files, then deletes them. I want to find the files "avant-window-navigator.*" and remove directories with the name "avant-window-navigator", i tried using the find command but i can't get it to work, and i don't want to remove them all manually.

---

### Post by erfahren on 2007-08-07
```

find ~/ -name \*~ -exec rm {} \;

find ./ -name \*~ -exec rm {} \;

```
the first example will find and remove the hidden backup files (textfile1~) in home directory, second in current dirctory

---

### Post by Inxsible on 2007-08-07
you can do a bunch of things

Go to synaptic and search for avant and mark for complete removal.
```
or  sudo apt-get autoremove awn
``` or will it be avant-window Change the package name appropriately. I dont know the exact package name.

Lastly the find command which only deletes ..does not uninstall is 

```
find /  -iname  avant-window-navigator.* -exec rm {} 
``` which will remove all files which are named avant-window-navigator from the / and not ask for your permission

```
find /  -iname  avant-window-navigator.* -ok rm  {} 
``` this will do the same except that it will ask you for each file if you want to delete it.

---

### Post by yogo on 2007-08-07
Man I wish I would have found this earlier!!!!!!!! I did manually delete all gazillion files of Avant Windows-Navigator this evening...what a pain. However I too had troubles with the uninstall as outlined in the AWN guide.

Have to copy these commands down for future problems, some of the programs will drop files all over and it is a pain to get rid of them, I may stick with Synaptic or Deb installer for easy removal. Thanks for the tips!

---

### Post by amrclutch1 on 2007-08-07
When I type in

```

find /  -iname  avant-window-navigator.* -exec rm {}

```

I get

```

find: missing argument to `-exec'

```

---

### Post by amrclutch1 on 2007-08-07
Nevermind I solved the problem myself.

---

### Post by pjman on 2007-08-26
> **amrclutch1 said:**
> Nevermind I solved the problem myself.

How? I'm getting the same error:

> find: missing argument to `-exec'

---

### Post by pjman on 2007-08-26
I just found that \ ; needs to be added at the end.


> find /  -iname  avant-window-navigator.* -exec rm {} **\ ;**

Can anyone explain why?

---

