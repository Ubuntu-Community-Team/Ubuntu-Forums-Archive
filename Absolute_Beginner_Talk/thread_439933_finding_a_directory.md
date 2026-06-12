---
title: "finding a directory"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-05-11
Hi
when a site says this:

'These files should be placed in your %OpenOffice.org%/user/template directory'

how do you go about finding this directory?

---

### Post by Najand on 2007-05-11
It is at you home:
~/.openoffice.org2/user/template

---

### Post by ubnewbie2 on 2007-05-11
You could search using a command line command called 'find'

e.g. to find anything with the string template in your home directory

find ~ -name *template*

---

### Post by Najand on 2007-05-11
Well, it is easier to use "locate" command.

---

### Post by ubnewbie2 on 2007-05-11
> **Najand said:**
> Well, it is easier to use "locate" command.

```
DESCRIPTION
       Secure Locate provides a secure way to index and quickly search for all
       files on your system  regardless  of  ownership.  It  uses  incremental
       encoding  just like GNU locate to compress its database to make search&#8208;
       ing faster, but it will  also  check  file  permissions  and  ownership
       before displaying matched entries so that users will not see files they
       do not have access to. Note that  permissions  and  ownership  are  not
       stored in the database.
```

Is it?  Seems overkill to create an indexed database of the files on your system, just to do a search.

---

### Post by Najand on 2007-05-11
It is enabled by default in almost all modern linux systems.
You are not supposed to update the database by yourself and the 
database is quite small. It is a fast easy and very famous way to 
find files and folders.

---

### Post by Jareth on 2007-05-11
yep, it was in my home directory, didn't realise it was hidden

Cheers for the help

---

