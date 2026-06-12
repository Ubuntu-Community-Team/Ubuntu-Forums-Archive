---
title: "how to find a word in a file (or files ) which is inside of a folder and subfolders ."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-14
how to find a word in a file (or files ) which is inside of a folder and subfolders ...

---

### Post by Inxsible on 2007-11-14
Do you mean a word in the file name or the word that is in a file?

if the former, you can use the find command```
find / -name "myfile" -type f -print 
```That will search for the file "myfile" in all the files under / (root). So basically all the folders and subfolders too.

You can add wildcards to the filename if you do not know the entire name of the file like so ```
find / -name "*myfile*" -type f -print 
```This will give you all the files that have the word myfile in ther names.

---

### Post by hooah212002 on 2007-11-14
Now that we have done that, how do you view the files?

---

### Post by Inxsible on 2007-11-14
> **hooah212002 said:**
> Now that we have done that, how do you view the files?

using your default text editor (provided of course that those files are text files)

Gnome = gedit
KDE = kedit
Xfce = mousepad

---

### Post by mokkai on 2007-11-14
> **Inxsible said:**
> Do you mean a word in the file name or the word that is in a file?

if the former, you can use the find command```
find / -name "myfile" -type f -print 
```That will search for the file "myfile" in all the files under / (root). So basically all the folders and subfolders too.

You can add wildcards to the filename if you do not know the entire name of the file like so ```
find / -name "*myfile*" -type f -print 
```This will give you all the files that have the word myfile in ther names.

i want to find the word that is in a file?

---

