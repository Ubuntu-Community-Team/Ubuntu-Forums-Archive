---
title: "how to delete something that wont?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-15
Hi

I recently tried to do a backup of my Ubuntu, but it started putting the backup **IN** my Ubuntu partition.  Now that caused me LOTS of problems and I have sorted them out now, but there is a 4.9GB .img file there which I want to delete but when I try to it says I cannot move it to the garbage bin because I do not have permissions to change it or its parent folder.

So how do I get permission?  It is in the file system  /  

Russty

---

### Post by Najand on 2006-09-15
Hmm, Open a terminal and run:
```

cd /
sudo rm -f <filename>.img

```
change <filename> with your filename.

---

### Post by Obor on 2006-09-15
I would start Nautilus as root and delete it from there 
i.e
Alt-F2
```
gksudo nautilus
```

Edit: too late :-)

---

### Post by Russty of Oz on 2006-09-15
WOW!  That was so easy!!  I guess that is to prevent you from deleting something important by mistake.

Thanks Najand!

Russty :D

---

### Post by Russty of Oz on 2006-09-15
> **Obor said:**
> I would start Nautilus as root and delete it from there 
i.e
Alt-F2
```
gksudo nautilus
```

Edit: too late :-)

I read the other one first, it worked, but it's nice to know there are other ways too.

Thank you.

Russty. :D

---

