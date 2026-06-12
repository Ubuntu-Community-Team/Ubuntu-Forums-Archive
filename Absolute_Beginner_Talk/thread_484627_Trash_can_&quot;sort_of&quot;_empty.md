---
title: "Trash can &quot;sort of&quot; empty"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-26
so, my trash can looks like it's full, says it contains 2 files. I look into it, nothing. Click the option to show hidden files, still nothing. Then i go into the command line, and this is what i get:


```
mark@laptop:~/.Trash$ ls -la
total 8
drwx------  2 mark mark 4096 2007-06-26 01:01 .
drwxr-xr-x 45 mark mark 4096 2007-06-26 00:25 ..
```

so, i have to cute little folders in there. And the real pain is, i cant remove them or even cd into them to see whats in there.


any ideas?

---

### Post by rillip on 2007-06-26
Erm, not sure about using the trash can, but 

```
sudo rm -r -f 2 
sudo rm -r -f 45
```

should take care of it.

---

### Post by colddayinapril on 2007-06-26
nope... nothing :(

---

### Post by romain.brenguier on 2007-06-26
It's normal you can't remove this 2 folders, 
they ( "." and ".." ) appear in all the directories.
"." is in fact the current directory and ".." the parent directory, 
you should be able to cd into them (try cd . or cd .. ).

I think your trash is really empty.

---

