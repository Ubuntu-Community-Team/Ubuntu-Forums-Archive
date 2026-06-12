---
title: "Anyway Ubuntu can handle .rar files ?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-06-10
There it is ??  Thanks !  ;)

---

### Post by yabbadabbadont on 2007-06-10
System->Administration->Synaptic Package Manager

Search for "unrar".  Install it.  Open up a terminal window and "man unrar" to learn how to use it.  :D

---

### Post by zvacet on 2007-06-11
```
sudo aptitude install p7zip p7zip-full rar unrar
```

Right click on file and select **unpack here**

---

### Post by yabbadabbadont on 2007-06-11
> **zvacet said:**
> ```
sudo aptitude install p7zip p7zip-full rar unrar
```

Right click on file and select **unpack here**

The only problem with that is that I don't think it will work with password protected rar files.  From what I've read in the forums, you pretty much have to use the command line unrar program to extract them properly.  But that is the only drawback I've heard about using your method.

---

### Post by Drakkor on 2007-06-11
Thx  	
yabbadabbadont 
will try it next time,lol :p

---

### Post by dokuro on 2007-06-20
is it the free unrar or the non free unrar

---

### Post by unclben on 2007-07-01
> **dokuro said:**
> is it the free unrar or the non free unrarBoth are in the repos, so you can install either unrar or unrar-free, whichever you prefer.

---

