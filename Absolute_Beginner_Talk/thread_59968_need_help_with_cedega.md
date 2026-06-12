---
title: "need help with cedega"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-08-26
Ok... i have the .tgz of cedega. how do i install it to my pc so i can play games on it???

---

### Post by jyank on 2005-08-26
transgaming has a .deb file of the latest cedega, i'd reccomend getting that, it will be easier to install.

---

### Post by servvs on 2005-08-26
so with the .deb would the command be something like dpkg /home/servvs/Desktop/cedega.deb?

---

### Post by jyank on 2005-08-26
after getting the deb, open up a terminal and type

```
sudo dpkg -i FILENAME.deb
```

if you have it anywhere other than /home/servvs then you will have to either:

1) ```
cd /home/servvs/Desktop
```

then the above code

2) ```
dpkg -i /home/servvs/Desktop/FILENAME.deb 
```

---

### Post by servvs on 2005-08-26
Ok.. i tried the .deb thing, and i got this error

dpkg: dependency problems prevent configuration of cedega:
 cedega depends on libasound2 (>> 1.0.9); however:
  Version of libasound2 on system is 1.0.8-1.
 cedega depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.

I looked for libasound2 on synaptic and didnt find anything... i have all the backports enabled as well. 

I also searched on the net and couldnt find much of anything. Does anyone know of where i could find it? or if there is a backport i didnt enable?

---

### Post by NumbSkullMD on 2005-08-26
I downloaded those two packages from the Debian website. I think one is from the unstable distribution. I think you'll also have to update locales as well...I did.

:?

---

### Post by servvs on 2005-08-27
[QUOTE=NumbSkullMD]I downloaded those two packages from the Debian website. I think one is from the unstable distribution. I think you'll also have to update locales as well...I did.

:?[/QUOTE]
 What do you mean "update locales"???

# sudo apt-get upgrade ?

---

### Post by RastaMahata on 2005-08-27
try to install cedega 4.4-1 version instead, works great on hoary. no dependency problems whatsoever.

---

### Post by NumbSkullMD on 2005-08-27
[QUOTE=servvs]What do you mean "update locales"???

# sudo apt-get upgrade ?[/QUOTE]
 The "locales" package...you'll need that from the debian site as well.

:?

---

### Post by pembo02 on 2005-08-29
where do you get the .deb packages
???

---

