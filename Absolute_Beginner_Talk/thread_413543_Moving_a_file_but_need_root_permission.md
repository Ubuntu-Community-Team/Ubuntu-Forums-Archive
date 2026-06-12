---
title: "Moving a file but need root permission"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-04-19
Hi I am trying to install Fmod, but I need to put a file into /usr/lib, 

How to I go about doing this?

Ian

---

### Post by 3rdalbum on 2007-04-19
Press Alt-F2, and type the following:

If you're using Ubuntu: 
```
gksudo nautilus
```

If you're using Kubuntu:
```
kdesu konqueror
```

If you're using Xubuntu:
```
gksudo thunar
```

Use that file browser to browse to /usr/lib. Now you can drag Fmod's file to /usr/lib.

---

### Post by dfox8895 on 2007-04-19
It seems that Fmod is a tar.gz file.   It is risky to install from source without following the instructions of the readme file or install file in the tarball.  In general this will be a slackware style install ( Tar, make, make install, ...etc.) I will go into more detail if needed but start there.

---

### Post by aysiu on 2007-04-19
> **dfox8895 said:**
> It seems that Fmod is a tar.gz file.   It is risky to install from source without following the instructions of the readme file or install file in the tarball.  In general this will be a slackware style install ( Tar, make, make install, ...etc.) I will go into more detail if needed but start there.
Or read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ianb72 on 2007-04-19
> **dfox8895 said:**
> It seems that Fmod is a tar.gz file.   It is risky to install from source without following the instructions of the readme file or install file in the tarball.  In general this will be a slackware style install ( Tar, make, make install, ...etc.) I will go into more detail if needed but start there.

Hi

There is not any readme or install file when I untar'ed it.

It was only for a game called Racer from [http://www.racer.nl/]("http://www.racer.nl/") 

Although it looks good it looks a pain in the bum to install everything, well it does to a newbie like me!! LOL :confused:

---

