---
title: "Changed ownder group over /usr and some subfolders :P"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by hecato on 2007-06-14
Hi there, I have been installing loot of things, the point is that now I was installing Cg toolkit from NVIDIA, the distribution is a compressed file and inside are the folders: bin, include, lib, local, share; the point is copy them over the /usr directory with root permission.

For do that I have done

```

gksu nautilus

```

I have copied the ./usr folder to /usr.... no problems in that way.

The problem come that I have uncompressed the files with my normal user account, then /usr /usr/lib and all the others now have tyoc:tyoc like owner:group!!!!!!



**My solution that _do thinsg worse_**!!!

Was first do in console

```

sudo chown root /usr -R

```

it apparently workd OK!!

and after


```

sudo chgrp root /usr -R

```


But in that momment I see what I have done!!!!

> 
sudo: must be setuid root
sudo echo "hi there"
sudo: must be setuid root




I havent set the root pass with passwd because I normally use sudo :D...

A guy sayed my that the root pass is the same than the user account, but havent worked, also suguested this page [http://tbynario.wordpress.com/2007/05/24/tutos-importantes-sobre-gnulinux/](http://tbynario.wordpress.com/2007/05/24/tutos-importantes-sobre-gnulinux/) that links to a way to recover root password here [http://www.adslayuda.com/Linux-root_passwd.html](http://www.adslayuda.com/Linux-root_passwd.html) I will do that in some moments...


The point is: **How to check if I havent breacked more of the installation**???? like I have done to sudo???, **how to chech that the file system under /usr is sane**??

---

