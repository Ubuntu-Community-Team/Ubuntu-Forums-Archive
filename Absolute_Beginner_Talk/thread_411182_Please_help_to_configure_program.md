---
title: "Please help to configure program"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-16
Hello, 

I need to configure my statistical program R so that I can install different 3rd source data sets.

Here's what I have to do but I don't know how to do it. Maybe someone can explain it to me in a primitive language?:

>>The normal setup on a Unix system is to install "user" packages in  
your home directory.

Here's what I do: create a directory tree ~/lib/R/library and then  
create a file ~/.Renviron with the following content:

    R_LIBS="~/lib/R/library:${R_LIBS}"

---

### Post by dstew on 2007-04-17
> create a directory tree ~/lib/R/library

Open a terminal window. You should already be in your home directory (symbolized by the ~ in the path). If not, you can get there by **cd ~**.

Enter at the command prompt:

```
mkdir lib
cd lib
mkdir R
cd R
mkdir library

```

> create a file ~/.Renviron with the following content:

R_LIBS="~/lib/R/library:${R_LIBS}"
Enter at the command prompt:
```
cd ~
nano .Renviron
```

That will open the text editor nano, with a file named .Renviron. Put in the line

R_LIBS="~/lib/R/library:${R_LIBS}"

Exit with writing the file, and you should be done. Because .Renviron starts with a dot character, it will normally be hidden in a directory listing. To see all the files in a directory, use **ls -a**.

---

