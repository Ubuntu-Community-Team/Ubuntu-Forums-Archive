---
title: "E: Couldn't find package linux-headers-2.6.9-10-amd64-generic"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-26
Hi, 

Any idea why this package isn't found? Maybe I haven't got the right repos?

[I]root@Ubuntu:/# apt-get install linux-headers-2.6.9-10-amd64-generic
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.9-10-amd64-generic[/I]

Thanks

---

### Post by bruce89 on 2006-06-26
Why are you running as root, it is extremely dangerous.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Brunellus on 2006-06-26
sudo apt-get install build-essential

---

### Post by bruce89 on 2006-06-26
[QUOTE=Brunellus]sudo apt-get install build-essential[/QUOTE]
Again, use *aptitude*
```
sudo aptitude install build-essential
```

---

### Post by ovimunt on 2006-06-26
Well, there's nothing I can brake. I'm using a spare HDD just for learning purposes. If I mess it up I'll just wipe it and start all over again. I guess trial and error is the only way to really learn.

Any suggestions for my error though?

---

### Post by bruce89 on 2006-06-26
[QUOTE=ovimunt]Any suggestions for my error though?[/QUOTE]
Yes, don't run as root.  You can use ```
gksudo nautilus
``` to get the file-manager in root mode.

---

### Post by ovimunt on 2006-06-26
Cool, thanks for the quick replys.

But... what's the difference between *apt-get* and *aptitude* ???

---

### Post by bruce89 on 2006-06-26
[QUOTE=ovimunt]But... what's the difference between *apt-get* and *aptitude* ???[/QUOTE]
See here - [http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by Brunellus on 2006-06-26
[QUOTE=bruce89]Yes, don't run as root.  You can use ```
gksudo nautilus
``` to get the file-manager in root mode.[/QUOTE]
totally unhelpful, and off-topic.

to the OP:  if you're looking for your kernel headers, install the build-essential package.  That will also install everything you need to compile programs.

---

### Post by Brunellus on 2006-06-26
[QUOTE=bruce89]See here - [http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)[/QUOTE]
it would appear that all the benefits of aptitude only fully accrue to those users who have never used apt-get.

---

### Post by bruce89 on 2006-06-26
I just noticed, the 2.6.9 kernel was never used in any Ubuntu release.  They were:
[LIST]
[*]Warty     2.6.8
[*]Hoary     2.6.10
[*]Breezy    2.6.12
[*]Dapper   2.6.15
[/LIST]
[QUOTE=Brunellus]it would appear that all the benefits of aptitude only fully accrue to those users who have never used apt-get.[/QUOTE]
Yes, but both I and aysiu recommend it.  Aysiu says that *gtkorphan* should be used to remove things that are orphaned.  In other words, for people who have only used apt-get.

---

### Post by ovimunt on 2006-06-26
Ok, ok, I'm out of root mode. Yet, why is it so dangerouls? I'm a COMPLETE BEGINER in linus.

Anyway, thanks for the tip of the kernel versions. ;) 

I also had a look at one of the error messages

*Can't find kernel sources in /lib/modules/2.6.15-25-amd64-k8/build;*

and decided to enter this command:

* sudo aptitude install linux-headers-2.6.15-25-amd64-k8*

and guess what? IT WORKS!!! It's downloading the package right now. :D 

Thanks again

---

### Post by Brunellus on 2006-06-26
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

