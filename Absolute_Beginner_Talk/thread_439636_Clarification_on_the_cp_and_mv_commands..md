---
title: "Clarification on the cp and mv commands."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-10
Hey. I've read the 'man cp' file, but I would like a bit of clarification:

cp /a/b/c.file /a/b/c2.file - This will copy c.file into the same directory, with the name c2.file, right?

cp /a/b/c.file /a/x/ will copy c.file into the x directory.

cp /a/b/* /a/x/ will copy all files from b into  x, right?

So, how about if i want to replace a directory with another one?

eg

cp /a/b/x/* /a/b/y/
then

rm -r /x ?

will:

cp -r /a/b/x/ /a/b/y/ do the same thing?

---

### Post by bukwirm on 2007-05-10
> **drowner said:**
> 
cp /a/b/c.file /a/b/c2.file - This will copy c.file into the same directory, with the name c2.file, right?

cp /a/b/c.file /a/x/ will copy c.file into the x directory.

cp /a/b/* /a/x/ will copy all files from b into  x, right?


Right.

> **drowner said:**
> 
So, how about if i want to replace a directory with another one?

eg

cp /a/b/x/* /a/b/y/
then

rm -r /x ?


That will work (be careful with rm, though).

> **drowner said:**
> 
will:

cp -r /a/b/x/ /a/b/y/ do the same thing?

Try it and find out (on a useless directory, of course).

---

### Post by drowner on 2007-05-10
Oh I see. (It copied the first folder into the second)

So, i think i've worked it, if your target IS a directory it will copy INTO it. So, no, thats not the way to do it.

---

### Post by drowner on 2007-05-10
> **bukwirm said:**
> 
That will work (be careful with rm, though).


Yeah, i see what you mean, i made an error up there. ;)

Fortunately there was no sudo or -f involved LOL

---

### Post by bukwirm on 2007-05-10
Sorry, I misread "replace a directory" as "copy one directory into another".

---

