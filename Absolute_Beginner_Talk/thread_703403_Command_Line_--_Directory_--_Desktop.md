---
title: "Command Line -- Directory -- Desktop"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Szdfan on 2008-02-21
I am trying to install Ndiswrapper onto my system.  Since I currently don't have the wireless drivers working, I downloaded the Ndiswrapper through my Vista boot and transferred it to the Ubuntu desktop.  I have extracted the file into a folder on my desktop.

Okay --

According to the walk through I'm following, I need to direct Command Line to the directory to the folder where I extracted Ndiswrapper.  I've been going through the Command Line help, but I can't find instructions on how to open directories or pull drivers from folders on the desktop.

Thanks,

---

### Post by y-lee on 2008-02-21
```
 cd ./Desktop
```

**Edit:** this assumes you are in your Home directory ;)

---

### Post by y-lee on 2008-02-21
Desktop is a hidden folder, to list all hidden files and folders use

```
ls -a
```

To see in Nautilus (ie ht file manger) click View --> Show Hidden Files

Hidden files have names that start with **. **like **.bashrc**

Folder names that are hidden also start with **.**

---

### Post by Pelham123 on 2008-02-21
Better to let ubuntu do the hard work for you. What was the file type extension? If you downloaded it in .deb format (from [http://ubuntu.packages.com](http://ubuntu.packages.com)) then you can 'mv' it to /var/cache/apt/archives/ then run synaptic or apt-get and let Ubuntu do the rest. Not sure if this method works for .gz files though


There is also this thread which will givew some pointers about installing Ndiswrapper from the Ubuntu install CD

[http://ubuntuforums.org/showthread.php?t=602584](http://ubuntuforums.org/showthread.php?t=602584)

---

