---
title: "Running my own program?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by ObeseOgre on 2006-06-21
I feel pretty bad for asking this... Im new to ubuntu and the words I searched pulled up too many irrelevent results.

I have a program I wrote called "scrabble.out" but when I try to run it by simply typing the name of it in the terminal i get "Bash: command not found"

Thanks

---

### Post by ape on 2006-06-21
Try running it as './scrabble.out'.  Note the leading dot (.) and slash (/).  In UNIX operating systems (unlike DOS and Windows), no directories are implicitly placed in the PATH.  The error you've received is because the OS doesn't know to search in your current directory for the program.  By telling it to run scrabble.out from the current directory (./), you should be successful.

---

### Post by Arndt on 2006-06-21
[QUOTE=ape]Try running it as './scrabble.out'.  Note the leading dot (.) and slash (/).  In UNIX operating systems (unlike DOS and Windows), no directories are implicitly placed in the PATH.  The error you've received is because the OS doesn't know to search in your current directory for the program.  By telling it to run scrabble.out from the current directory (./), you should be successful.[/QUOTE]

If you do want your current directory (wherever you are) to be in the PATH, just add it:

```
export PATH=$PATH:.

```

After this, you can write just "scrabble.out", and it will be run.

If you want just this particular directory which "scrabble.out" resides in to be added to the path, find out the name of it and then add it:

```
% pwd
/home/me/scrabble-development
% export PATH=$PATH:/home/me/scrabble-development
%

```

---

