---
title: "$ find . -exec chown carl {} \;"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-15
From my System V Unix days in the 1980's, I never forgot this command:

$ find . -exec chown carl {} \;


Its quite cyptic but very powerful.  You sweep through all subdirectories and execute a command.

Then there is:   find . -name *.c -print
which sweeps through all subdirectories and outputs all files with the .c extension.

My question -- even though these still works with Ubuntu Linux,  is there a better command?

Carl

---

### Post by steve.horsley on 2007-11-15
I think 
**chown -R carl * **
will do the same thing.

---

### Post by schorsch on 2007-11-15
... and regarding the second part: After installing the package "slocate" and running the command
```
updatedb
```
you will be able to search for files systemwide via
```
locate .c
```
... I used ".c" just to keep your example. Substitute it with anything you want to look for.

---

### Post by javaguru on 2008-02-18
> **schorsch said:**
> ... and regarding the second part: After installing the package "slocate" and running the command
```
updatedb
```
you will be able to search for files systemwide via
```
locate .c
```
... I used ".c" just to keep your example. Substitute it with anything you want to look for.

yes, slocate (locate *.c) is a good way to find files, but can it be used in cojunction with other commands as above, such as locate *.foo -exec bar ? Now i know that -exec doesn't work on locate

---

### Post by javaguru on 2008-02-18
> **cwmoser said:**
> From my System V Unix days in the 1980's, I never forgot this command:

$ find . -exec chown carl {} \;


Its quite cyptic but very powerful.  You sweep through all subdirectories and execute a command.

Then there is:   find . -name *.c -print
which sweeps through all subdirectories and outputs all files with the .c extension.

My question -- even though these still works with Ubuntu Linux,  is there a better command?

Carl

Carl could You please explain the above command ? I don't particularly understand the paranthesis and the "\;" why exactly are they there ?

---

### Post by Claus7 on 2008-04-16
> **javaguru said:**
> Carl could You please explain the above command ? I don't particularly understand the paranthesis and the "\;" why exactly are they there ?

Hello,

I just came accross this post. The answer is the following :
```
$ find . -exec chown carl {} \;

```
find in the directory that this command is executed and in all the subdirectories of that directory (that is what the . here means) 
all the files ({}) and 
execute (-exec) the command 
chown carl (change the owner of all these files to carl).
The arguments of the exec command are up to ; symbol and we escape that symbol with '\' in order to be protected from being expanded by the shell.

Hope this was clear,
Regards!

---

