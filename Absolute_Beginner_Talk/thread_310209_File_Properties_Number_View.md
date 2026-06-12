---
title: "File Properties Number View"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-30
Sorry to ask another elementary question, to which I ought to be able to find the answer, but I've searched for a while.  In the nautilus File Properties box, Permissions tab, I don't understand part of the "Number view."  I can see that the last four digits represent the permissions as used in a "chmod" command using numeric mode, but can't make anything out of the first three digits.  

Also I can't find an explanation of the first piece of output from the ls -l command.  The first line says "total x" where x is an integer.  It's obviously related to the number of files/directories in the parent directory but I can't figure out what it means.

Any help appreciated.

Buck

---

### Post by Buck2348 on 2006-12-04
A little bump.  Some of you smart people know the answers.  Thank you.

Buck

---

### Post by bodhi.zazen on 2006-12-04
It depends.

If the listing is a directory, the first number is the number of directories within it (.. counts as 1).

If it is a file, it is the number of links to the file itself.

---

