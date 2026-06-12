---
title: "Chmod"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2006-12-23
What command using chmod would I use to change the permissions of the WWW file?

---

### Post by BatteryCell on 2006-12-23
What permissions do you want to change?

its (assuming that /var/www/ is the www you refer to):
```

chmod ### /var/www/

```
Where the three #s are the permissions you want to give to owner, group, and others.

---

### Post by 4.9 on 2006-12-23
So I do Chmod group write /var/www/?

---

### Post by punx45 on 2006-12-23
like i said in the other thread:

```
man chmod
```

but keep in mind that if you change permissions of the folder so that you can write to it when you are not the owner, then anyone else on the system can too.   possibly a glaring security hole.

i changed ownership of /var/www to my own username rather than root, so that way, the world permissions are still read only and i have easy access to the folder.   so for to figure out how to do that  ```
man chown
```

---

### Post by punx45 on 2006-12-23
if you ```
ls -l test.html
```

you get

> merom:~ geoff$ ls -l test.html
-rw-r--r--   1 geoff  geoff  127258 Nov 16 19:59 test.html

the names after the number identify the owner, and then group association of the file.   so i am the owner of the file.

to allow others to write to the file i need to add a w in the third set of rwx

so i 
```
chmod 645 test.html

or 

chmod o+w test.html
```

where o stands for other and w for write.



chart sort of thing!```


4 2 1   4 2 1   4 2 1
r w x | r w x | r w x 
  o         g        w
  w        r         o
  n        o         r
  e        u         l
  r        p         d



```


this is probably just as confusing... i recall having a little dificulty understanding how chmod works at first.   best is to just play around with it, keep referring to the man page,  etc.


and here is what chown looks like.   i changed the owner from root to myself:
```
merom:~ geoff$ ls -l test.html
-rw-r--rw-   1 root  geoff  127258 Nov 16 19:59 test.html
merom:~ geoff$ sudo chown geoff test.html
merom:~ geoff$ ls -l test.html
-rw-r--rw-   1 geoff  geoff  127258 Nov 16 19:59 test.html

```

---

### Post by Atomic Dog on 2006-12-23
chmod 777 all the way!  OK not really.  If you're a lazy person like me and hate to type cryptic commands just right click the file in nautlilus and change the permissions that way.  Youu may possibly have to run nautilus as root (terminal window then sype gksudo nautilus) to change some of the files.

---

