---
title: "want to tar a directory and all subdirectories [Resolved]"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Mateo on 2007-02-26
I couldn't figure out how to do this.  I want to tar a directory that i'm in, just the *.tex files, and all subdirectories (also the *.tex files).  So far I have this:

```
tar cvf foo.tar *.tex
```

but that only does the current directory.  thanks.

---

### Post by justifier on 2007-02-26
the easiest way is to navigate to it in a file manager right click and click on create archive, and follow the on screen instrustions

---

### Post by Mateo on 2007-02-26
yeah but i'd rather do it from the command line so I can create a script out of it so it will all happen with one command.

---

### Post by punx45 on 2007-02-26
in the example you gave you are giving tar specific file names within a directory rather than the whole directory.   i think this is why you are not getting files from subdirectories.

how to actually get it to do what you want is another story, and unfortunately i dont have an answer, but im sure someone that does will come along soon.

---

### Post by Mateo on 2007-02-26
bump, anyone know how to achieve this?

---

### Post by WW on 2007-02-26
Just give the name of the directory to tar.  For example, suppose you want to create a tar file for all the files (including all subdirectories) in the directory called myfiles. Give this command from the directory that contains myfiles:
> tar cvf myfiles.tar myfiles
To check the list of files in the tar file, you can use the **t** option.  For example,
> tar tf myfiles.tar | less 

EDIT: Whoops... I just reread the original post a bit more carefully.  These commands will put all the files into the tar file, not just the .tex files.

Here is one possible way to get just the .tex files.
> find myfiles -name "*.tex" > /tmp/texfilenames
tar cvf myfiles.tar --files-from /tmp/texfilenames
The **find** command is used to create a list of all the file names that end in .tex.  The **--files-from** argument to tar is then used; this tells tar to only archive those files listed in /tmp/texfilenames.

---

### Post by Mateo on 2007-02-27
that achieves the desired effect, thanks.

---

