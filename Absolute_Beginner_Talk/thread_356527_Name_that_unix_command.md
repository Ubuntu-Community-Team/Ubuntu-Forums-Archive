---
title: "Name that unix command"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by otakuj462 on 2007-02-08
Hi, I'm trying to recall what is the unix command that takes another command, and tells you where it is located in your filesystem. I ask because I'm trying to locate alsactl, and unbelievably it's not anywhere in /usr/! That is to say:
```

jacob@jacob-laptop:/usr$ find -name alsactl
                       
```
returns nothing.
Let me know. Thanks.

---

### Post by Fundi on 2007-02-08
You could try this although i'm not sure if it what you want:

```
# whereis alsacti
```

---

### Post by antenna on 2007-02-08
whereis?

edit: too late :)

---

### Post by schorsch on 2007-02-08
Hi,

```
find / -name alsactl
``` should do the trick. 

```
whereis alsactl
``` will work, if the package "util-linux" is installed.

Another way to find files is

```
locate alsactl
``` if the the package "slocate" is installed.

The advantage of the locate command is that normally once a day your system is searched for files and the location of the files is stored in a tiny "database" whereas the find command searches the whole system right at this moment and therefore takes a longer time to execute.

---

### Post by n0ll on 2007-02-08
if alsacti is in echo $PATH then

which alsacti 

will return the location (i.e. path) of/to  alsacti 

EX:

```
which alsacti 
which man
which ls
which grep
which which
```

---

