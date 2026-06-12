---
title: "[SOLVED] Only Directories"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-12-05
Using the command line I was wondering if there is a simple solution to list only directories or only file in a given directory. I searched the net but the commands seems pretty complex for a simple job like this.

---

### Post by n00buntu_tim on 2007-12-05
ls -d

---

### Post by jken146 on 2007-12-05
You can do ```
ls -d
``` to list just the directories.

A good way to find out about the options for a command is to do ```
man <command>
```, e.g. "man ls" or "man chown".

---

### Post by n00buntu_tim on 2007-12-05
"Give a man a fish, and you feed him for a day. 
    Teach a man to fish, and you feed him for life."

---

### Post by mahiyar on 2007-12-05
With ls -d you get a nice . (dot), at least thats what it gave me (try it). Since I cannot find in man pages Iam asking here in the forum. The obvious is not always so.

---

### Post by mikewhatever on 2007-12-05
> **mahiyar said:**
> With ls -d you get a nice . (dot), at least thats what it gave me (try it). Since I cannot find in man pages Iam asking here in the forum. The obvious is not always so.
Man pages for ls would show if you do <man ls>. I also get a dot when running ls -d in my home. Odd.

---

### Post by stchman on 2007-12-05
> **mahiyar said:**
> Using the command line I was wondering if there is a simple solution to list only directories or only file in a given directory. I searched the net but the commands seems pretty complex for a simple job like this.

Use the following command

```
ls -l -d */
```

This will give your just directories.

This website is a big help.

[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

---

### Post by mahiyar on 2007-12-05
Thanks stcman, that was exactly what I ws looking for. Now only if somebody can tell me to list only files, I will be satisfied. BTW thats an excellent site, better then man pages and with examples too.

---

### Post by n00buntu_tim on 2007-12-05
> **mikewhatever said:**
> Man pages for ls would show if you do <man ls>. I also get a dot when running ls -d in my home. Odd.

So do I - this is rather unexpected...

---

### Post by n00buntu_tim on 2007-12-05
man page:

       -d, --directory
	      list directory entries instead of contents, and do not  derefer-
	      ence symbolic links

My apologies - I'll get back in my box.

---

### Post by mahiyar on 2007-12-05
No need to apologise or anything, we are all learners and in the same boat. (Ubuntuboat) :):)

---

### Post by stchman on 2007-12-05
> **mahiyar said:**
> Thanks stcman, that was exactly what I ws looking for. Now only if somebody can tell me to list only files, I will be satisfied. BTW thats an excellent site, better then man pages and with examples too.

To list only files in a particular directory do the following:

```
ls -l | grep -v "^d"
```

If you don't like the "//" after the directory in the directory only then use this command:
```
ls -l | grep "^d"
```


I hope this helps.

---

### Post by phorgan1 on 2008-07-17
I use this all the time, shows a nicely formatted list of directories in the current directory.

alias lsd='ls -d `find . -maxdepth 1 -type d -print | grep -v "^.$" | cut -c 3- `'

If you want an alias for files only, lsf, try this:

alias lsf='ls -d `find . -maxdepth 1 -type f -print | grep -v "^.$" | cut -c 3- `'

Note the backquotes, they are important.  The alias syntax works in bash and sh,

If someone can come up with a shorter more elegant version, perhaps using sed to replace the grep and the cut, please let me know:)

Patrick

---

