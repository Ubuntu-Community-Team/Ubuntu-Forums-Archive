---
title: "Shell Script - Run command for all files and subdirectories"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-21
I'm just new to linux so I don't know much about shell scripts and such, but I figured out some commands by trial-and-error and I think I know what I want, but can't do it myself.

Basically, I want to rename all files in a certain directory, including all the files in the subdirectories, by making them all lowercase and changing spaces to _. (This is basically to rename my music folder copied from windows)

I figured out two commands to help me do this:
```
rename -f  y/A-Z/a-z/ *
rename -f  y/\ /_/ *
```

As also delete all extra files in that folder (The extra files windows media player created)
```
rm *.jpg
rm desktop.ini
rm thumbs.db
```

This will be sufficient for my requirement, but unfortunately this does not go deep into subdirectories. It only works for the files in the current dir. How do I make it go into all subdirectories under the current dir? I think a shell script is required for it but have no clue what to do.


Note: I tried searching for similar threads here, I found someone refering to a Nautilius script, but I'm running Kubuntu 6.06, and don't know about any Konqueror scripts.

---

### Post by Arisna on 2006-11-21
Look into the command "find".  It will allow you to traverse subdirectories, printing all or some filenames to standard output.  You can then use a pipe ("|" character) to redirect the output of find into rename.

Edit:  There is an application native to KDE called KRename that can handle batch renaming through the GUI, but you might want to try the command line way first if you are interested in learning the command line in more depth.

---

### Post by Verminox on 2006-11-21
Yes indeed I would rather learn the CLI way.

How exactly would I use the pipe character to redirect std output? An example would help. :)

Edit: Nevermind, got it. Just need to find how to filter results found by find now.

---

### Post by Verminox on 2006-11-21
Why does the rm command not work with find?

find . | rename -v -n [expr]
... works

find . | rm
... does not work

If i specify conditions for rm like *.jpg it works only for the current dir, not for the results that find has found.

How do I delete files based on find's results?

---

### Post by nanotube on 2006-11-21
look here, this might be helpful: :)
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Removing_a_large_number_of_files](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Removing_a_large_number_of_files)

---

### Post by zekopeko on 2006-11-21
> **Verminox said:**
> Why does the rm command not work with find?

find . | rename -v -n [expr]
... works

find . | rm
... does not work

If i specify conditions for rm like *.jpg it works only for the current dir, not for the results that find has found.

How do I delete files based on find's results?

try rm -R /name/of/the/folder

that should remove recursively everything in a directory and it's sub-directorys

---

### Post by Verminox on 2006-11-21
nanotube: Beautiful. Thanks.

---

### Post by IYY on 2006-11-21
To answer the original question... If you want to apply a command to a directory recursively, use find. Here's how:
```

find . -exec echo {} \;
```

The above code will execute the command "echo" on every filename in the current directory, and all subdirectories recursively. The . means `current directory' (you could put any directory name instead of it), `echo' is a command you want to execute. {} is like a variable that represents the filename for each file.

---

### Post by enopepsoo on 2008-07-05
> **IYY said:**
> To answer the original question... If you want to apply a command to a directory recursively, use find. Here's how:
```

find . -exec echo {} \;
```

The above code will execute the command "echo" on every filename in the current directory, and all subdirectories recursively. The . means `current directory' (you could put any directory name instead of it), `echo' is a command you want to execute. {} is like a variable that represents the filename for each file.

Thanks for posting this.  It was helpful for me.

---

