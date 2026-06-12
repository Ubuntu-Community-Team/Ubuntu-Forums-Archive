---
title: "Application Launcher"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-08-09
Hi,

I've created an application launcher for my folding@home, however whenever i launch the app it creates the files/directories in my home directory rather than the directory of the actual executable. Is it possible to issue a command to make it think that I'm launching the program from inside its own folder?

Basically when I launch it, it says:

```
Launch directory: /home/jexel
Executable: /home/jexel/Folding/FAH504-Linux.exe

```

Is it possible for the launch directory to be /home/jexel/Folding ?

Thanks a lot in advance.

---

### Post by Gabn on 2007-08-09
it leaves the work files/directories in whatever folder you launch the program from. (from memory) 

so cd into the Folding directory 
then ./FAH504-Linux.exe 

and it should just create files in that directory.

---

### Post by Jexel on 2007-08-09
Well that's why i created a launcher in the panel so i don't have to open up a terminal, cd into my directory and then running folding@home. Rather I can just click on the launcher and expect it to work.

---

### Post by RomeReactor on 2007-08-09
Hi. Try writing this in the **Command** entry for the launcher:
```
sh -c "cd /home/jexel/Folding && ./FAH504-Linux.exe"
```

---

### Post by Jexel on 2007-08-09
you are awesome. Thanks a lot!

---

