---
title: "run application dialog acts strange."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by atomkarinca on 2007-08-06
the run application dialog isn't running the files, instead it's openening the folders containing the files. why is that?

---

### Post by finer recliner on 2007-08-06
you probably need to define a program to open the file with (just like you would in the terminal).

for example:
```

gedit /home/user/file.txt

```
^you want to open file.txt with gedit (a text editor).

by typing just 
```
/home/user/file.txt
```
the shell doesnt know what to do with that file, so it probably just defaults to opening it with nautilus (or konqueror or whatever you're using)

nautilus and konqueror and other GUI filesystem navigators assign default programs to launch certain file types. the command line doesn't.

---

### Post by atomkarinca on 2007-08-06
alright, let me clear things out :) this happened to my friend he doesn't have internet right now. the problem is this: for example you want to open a program, let's say amarok. when he types amarok in the run application dialog (ie. alt+f2) only he gets is the folder containing the file. i never had this problem and couldn't find a solution on the internet so i gave it a shot here.

---

