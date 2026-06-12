---
title: "delte a user name but cannot"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-08
I inadvertedly created a user account last week in
var/lib/redon
redon is the user name

this has three directoys one of which has only root access
how to delete these directories and the files in them from command line

what is the command line to deltere a entire directory.

I will create the user name again in my home directory

if i go to applications and users and delete from there it keeps coming back
so want to delete these directories permanently.

lex1:???: :???:

---

### Post by Moebius on 2006-03-08
to delete a directory from command line you can do this
```
rm -Rf folder/
```

as one of them needs root privileges, then you must do this
```
sudo rm -Rf folder/
```

the **R** option is for Recursive mode
the **f** option is for Force delete

if you need further informations, do this in the command line
```
man rm
```

Cheers

---

### Post by Klaidas on 2006-03-08
to delete a directory type ```
rmdir
``` (if it's empty)
else, ```
rm -rf /where/you/dir/is
```

But... [COLOR="Red"]BE EXTRA CAREFUL WHEN USING -rf. It can brake your entire system if you are not careful[/COLOR]

---

