---
title: "Help Installing Tar Files"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-06-06
I need help installing Tar files  Tar.gz files

---

### Post by aeiah on 2007-06-06
you dont install tar.gz files, they're just an archive/container, like .zip or .rar

you may need to install the contents of the tar.gz though. have you downloaded something in source that needs compiling?

---

### Post by NeoLithium on 2007-06-06
Well, usually there is a readme file inside the file, so you can just open up a terminal window, CD to the directory where it is saved. (Firefox usually drops it on the desktop, so that's what I used in the example below)
```

cd /Desktop

tar -xvzf FILENAME.tar.gz

```

That will unzip the file and allow you to enter the directory to view the readme on what is required to be done to install :)  Of course you can also right click on it and select Extract Here, if you prefer the GUI way...

---

### Post by jazzman84116 on 2007-06-06
I want to install this avant-window-navigator-0.1.1  .  I tried to follow the tutorial in how to install anything in ubuntu  but I still cant get it to work

---

### Post by jazzman84116 on 2007-06-06
This is the read me file from it 

avant-window-navigator	0.1.1

./autogen.sh --prefix=/usr && make && make install

enjoy!!

launch with avant-window-navigator OR Applications->Accessories->Avant Window Navigator

configure with avant-preferences OR System->Preferences(->More Preferences)->Avant Preferences

-Neil

---

### Post by NeoLithium on 2007-06-06
Hmmm, Avant can be tricky from time to time, however this thread is a nice walkthrough for it. You can just skip the affinity stuff if you don't want that added:
[http://ubuntuforums.org/showthread.php?t=385981&highlight=How+To+Install+Avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=How+To+Install+Avant)
Hope this helps

---

