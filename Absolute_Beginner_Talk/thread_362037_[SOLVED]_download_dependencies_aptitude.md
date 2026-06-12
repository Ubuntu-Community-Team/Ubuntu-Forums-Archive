---
title: "[SOLVED] download dependencies aptitude"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-02-15
Hi guys , I recently came to know about the command :
sudo aptitude download <packagename>
it downloads the package as a .deb file in my home directory (which is very good).

Now the question is that i need to install most of the packages on a friend's PC and he doesnt have an internet and the only way he is going to get packages is by CD. So is there any way that i can get the package as well as the dependencies it needs(Like sometimes some packages require installation of some other packages) with a single command ?
I hope u get my question.
Thanks

---

### Post by kane77 on 2007-02-15
sudo apt-get build-dep -d package_name

---

### Post by ashmew2 on 2007-02-15
OK i ran that but i do not know where all the packages went . after it finished it said "in Download Mode only" 
BUt where are the packages!?!?!?!

---

### Post by ashmew2 on 2007-02-15
Thanks man , i found it using the command :
```

locate vorbis-tools 
```

(i had selected it as the package when i used apt-get)

It was in```
 /var/cache/apt/archives/
```

---

### Post by ashmew2 on 2007-03-22
Hi..is there ne way to download dependencies of different packages into different folders but only downloading those which havent been downloaded before...any way to omit the already installed packages and download dependencies to different folders ?
Also..the command i have been using only downloads the dependencies and not the main package itself (i tried amarok and it was still saying it required the addition installation of 6 packages)..
Any commands to resolve this issue.

THankz

---

