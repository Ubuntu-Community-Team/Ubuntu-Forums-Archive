---
title: "ls syntax"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-05-01
I have one directory which has lots of sub directories at the next level down.  I would like to save a file which lists all of those sub directories.

I want the output as a simple list and the output in say a .txt. I cannot quite see how to pipe the output to a file.  This must be easy ... any suggestions appreciated :)

---

### Post by kano on 2007-05-01
Just add a "> filename.txt" to the end of your command :)

---

### Post by freebeer on 2007-05-01
how about:

```

ls -alR > files.txt

```

the "ls -al" lists the files in a particular format that I like.  The "R" (note that it is case sensitive) means to do so recursively... ie... do it for all subdirectories relative to the current directory.  the ">" redirects the output to a file called "files.txt"

I think that's what you're looking for.

---

### Post by ofek on 2007-05-01
Its not what he was asking and its ">>".
Anyway as to the problem I can't really help because pipes and shell scripting isn't my common ground though I remember doing something like this with echo piped with something ages ago.
Have a quick look at the command reference im sure ull find something useful thats what I do when I seek answers..

---

### Post by expatCM on 2007-05-01
Wow ... so many responses and so fast.  Thank you all :)

---

### Post by freebeer on 2007-05-01
> **ofek said:**
> Its not what he was asking and its ">>".


The ">>" appends (adds to) an existing file.  The ">" will overwrite the contents of the file with the newer data.  Given that he's wanting to create a text file containing the list of files in his directories, it generally doesn't make sense that he'd want to append data - he's only interested in the current information.  But I will agree that that's my interpretation of things.  :D

---

