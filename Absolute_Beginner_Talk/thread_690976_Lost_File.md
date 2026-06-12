---
title: "Lost File"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-02-08
I lost a veggie tale movie called Pirates something that I downloaded via Azureus.  I've literally looked everywhere and cannot find this movie.  I played it once but thats because within Azureus i chose "Open File location" or whatever.  It brought to some folder that I don't remember and since then I cannot find it.  I accessed it a few times via "recent documents" but that was over a month ago.  I've searched dozens of times but I can't find it anywhere.  I'm 100% sure I didn't delete but I have no idea where it went!!!

Help?

---

### Post by amo-ej1 on 2008-02-08
Open a terminal and type 

find ~ -name "*irates*"

Azureus has probably hidden it somewhere in your users home directory, and above command will print all files in your home directory which have the string 'irates' in their name.

---

### Post by cartisdm on 2008-02-08
> dan@dan:~$ find ~-name "*irate*"
find: ~-name: No such file or directory
find: *irate*: No such file or directory
dan@dan:~$ 


Nothing:( I'm pretty sure it was a .AVI file, can I do a search for all my .AVIs?


Edit:  Found it using 

> Locate "*irate*"

I don't know much about the terminal so I have no idea why that works but thanks!

---

### Post by cknight on 2008-02-08
You need a space between the '~' and the '-name'.

---

### Post by cartisdm on 2008-02-08
> **cknight said:**
> You need a space between the '~' and the '-name'.

gotchya

---

### Post by amo-ej1 on 2008-02-08
As a sidenote, 'locate' search a prebuild database which is build using a command called updated. Locate is typically faster than find, but if your database (which is build daily) is out of date you won't find it.

Find goes typically slower, but really searches the contents, so it doesn't rely on a database.


Sidenote on the sidenote, updatedb uses find to build the database ;)

---

### Post by zvacet on 2008-02-08
If you want to search all your filesystem then you have to be on top of it with **cd /** command.After that 

```
sudo find / -name *filename*
```

---

