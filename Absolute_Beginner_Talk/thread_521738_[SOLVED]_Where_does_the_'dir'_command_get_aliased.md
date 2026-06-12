---
title: "[SOLVED] Where does the 'dir' command get aliased?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Contrarian on 2007-08-09
I don't see it in my .bashrc profile or other startup scripts.  I'd like to change it to 'ls -all'.

---

### Post by Redache on 2007-08-09
Try [Here]("http://www.hypexr.org/bash_tutorial.php#alias")

---

### Post by jjefferies on 2007-08-09
look in /etc and double check man bash as to the order of startup scripts.

---

### Post by K.Mandla on 2007-08-09
/etc/profile? I'm not on Ubuntu right now, or I'd try it out and see.

---

### Post by schorsch on 2007-08-09
It seems to be not an alias as there is a binary located in /bin:

```

schorsch@schorsch-linux:~$ which dir
/bin/dir
schorsch@schorsch-linux:~$ ls -l /bin/dir
-rwxr-xr-x 1 root root 81820 2007-03-05 07:25 /bin/dir

```

... and there is a manpage for this command, too ....

---

### Post by Contrarian on 2007-08-09
> **schorsch said:**
> It seems to be not an alias as there is a binary located in /bin:



Indeed you are correct.  In fact they look like they are the same program (the man pages look very similar but I didn't do complete check).  What a silly silly thing to do.

---

### Post by fastpakr on 2007-08-09
If it's just a copy, why does 'ls' color code the results but 'dir' does not?

---

### Post by Contrarian on 2007-08-10
> **fastpakr said:**
> If it's just a copy, why does 'ls' color code the results but 'dir' does not?

I guess they aren't copies then, but does the default installation really need two programs that essentially do the same thing.  I'd think an alias within the profile for dir to ls would be just as good and more along the unix/linux best practices. 

just my 2c

---

