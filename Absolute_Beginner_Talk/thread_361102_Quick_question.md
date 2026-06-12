---
title: "Quick question"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by NooBeee on 2007-02-14
Just out of curiosity - What does  ./  really mean? Why do I have to type it in order to run stuff?

---

### Post by nickoli_02 on 2007-02-14
The .  means starting from the current directory. The / is just, um, unix directory structure I guess. You can get away with never using ./ if you like. The following two lines are equivalent, assuming there's an executable script runme.sh in the folder /tmp, and your current working directory is /tmp:

./runme.sh
/tmp/runme.sh

---

### Post by Jucato on 2007-02-14
1. What does it mean?
. - means the current (also called "working") directory or location
/ at the end of a name means that the name stands for a directory (like "foo/" would mean foo is a directory)
Taken together:
./ - current (the '.') directory (the '/' at the end of the name)
./foo - run the file named "foo" that is located in this (current) directory.

2. Why do you need this to type "./foo" and not just "foo"?

Linux follows a certain sequence of what directories to search into for programs/scripts/executable files. This sequence is stored in a variable named PATH. Typing 

```
echo $PATH
```

in the terminal (gnome-terminal or konsole) will show you which directories are searched and in what order. So when you type in a filename, Linux will look into each of those directories in PATH one by one, until it finds that filename and executes it. If you notice, the current directory (represented by ./) isn't in the PATH. which means that the current directory is not searched first. In fact, it is never searched at all. You have to explicitly tell Linux that the program you want to execute is in the current directory. And the shortest way to do that is by using "./file". Of course, it's only one of the ways. You can also tell Linux the location by giving the exact path to the file, like "/home/username/bin/file.sh", if the file you want to run, named file.sh, is located in /home/username/bin.

---

