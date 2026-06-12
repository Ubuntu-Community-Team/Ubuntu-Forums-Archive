---
title: "how do i install java runtime environment"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-07-14
I have downloaded jre from a website and have .bin folders on my desktop.  how do I install jre so as to actually use it?

---

### Post by Brunellus on 2006-07-14
please see this wikipage for help with Java installation...

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Paerez on 2006-07-14
don't do it that way, you can do it the easy way.
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

or through synaptic, search for JRE and install sun's.
EDIT: see post right below this one

---

### Post by Jagot on 2006-07-14
It's in the repos - you do not need to download it separately.  Enable the multiverse repo:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then:

```
sudo aptitude update
sudo aptitude install sun-java5-bin
```

---

### Post by bruce89 on 2006-07-14
Plenty of conflicting ways, the 3rd one is best, but slightly wrong.  It should be
```
sudo aptitude update && sudo aptitude install sun-java5-jre
```

---

### Post by Jagot on 2006-07-14
> **bruce89 said:**
> Plenty of conflicting ways, the 3rd one is best, but slightly wrong.  It should be
```
sudo aptitude update && sudo aptitude install sun-java5-jre
```

Well, it's the one recommended in the wiki and has always worked for me:

[https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e](https://help.ubuntu.com/community/Java#head-21b44ff330436e9f387606a337f458a3c2113a3e)

---

### Post by avtolle on 2006-07-14
Both will accomplish the same thing.:)

---

### Post by qdvubun on 2006-07-14
its also an option in automatix, you can just check it and it will do the rest

---

### Post by Soap_Dude on 2006-07-14
I just recently installed it with the bin file. The synaptic idea is good one, but since you've already got the bin file(I'm assuming it's the right one), you can do it with a couple of simple commands. Move the bin file to the folder you want to install it. Probably /usr/local/bin/. You will probably need root access to write to that folder. Then in terminal give yourself the permission to execute the bin file
```

sudo chmod +x jre*.bin

```(or whatever file name it is, I use the '*' wildcard because the file name is too long) 

then run the executable
```

./jre*.bin

```

the executable will be default install in the folder that it is in.

Hope this helps ;)

---

### Post by Jagot on 2006-07-14
Synaptic is the manages the packages well and thus it is always preferable to check if something is available in the repo's first.  If you install it manually, when any updates come along you will have to install them manually.  If you install via Synaptic, it will handle this for you.

---

