---
title: "ls and/or dir problem."
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by lurah on 2006-05-02
Hi all.

I have tryed to find out how to "ls" or "dir" files or folders only in console.
--help and google havent helped me on this. ](*,) 

Is it possible to do it?
I just want files at files.tmp and folders at folders.tmp by using "> filename.tmp"

Thanks

---

### Post by AnRuaRi on 2006-05-02
not 100% sure what you're looking for
you looking to list only the directories in a given directory, (or only the files, but not the directories)?

ls *.*
will list all files in current directories, but not the folders or symbolic links (shortcuts)

I cant seem to find how to list just the directories

---

### Post by hw-tph on 2006-05-02
I love the "find" command. To find all the dirs in the current directory, type **find . -maxdepth 1 -type d**, or replace "-type d" with "-type f" to find regular files only. You could alias them (in your ~/.bashrc) to have easy access to these commands:
```
alias lsd='find . -maxdepth 1 -type d'
alias lsf='find . -maxdepth 1 -type f'
```

...or you could just type **ls -d */**
:)


Håkan

---

### Post by nanotube on 2006-05-02
looks like you are in need of some basic knowledge of the commandline. click on the link in my sig, and go to the section titled "other command line resources". you will see a list of some nice commandline tutorials.

---

### Post by catlett on 2006-05-02
[QUOTE=nanotube]looks like you are in need of some basic knowledge of the commandline. click on the link in my sig, and go to the section titled "other command line resources". you will see a list of some nice commandline tutorials.[/QUOTE]
Nanotube your a wealth of knowledge. I'm just going to follow your posts tonight and threefold my linux knowledge. Thanks for the link I never saw that before.

---

### Post by nanotube on 2006-05-02
[QUOTE=catlett]Nanotube your a wealth of knowledge. I'm just going to follow your posts tonight and threefold my linux knowledge. Thanks for the link I never saw that before.[/QUOTE]
hehe thanks for your compliment catlett. :)

---

