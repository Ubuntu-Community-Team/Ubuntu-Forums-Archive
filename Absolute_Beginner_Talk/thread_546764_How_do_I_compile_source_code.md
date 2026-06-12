---
title: "How do I compile source code?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-09
Hi, there is another post with this same title, I read it and it something to do with getting wine compiled.

Could some one give me a fool proof guide on how to compile stuff? So lets say I download "program.tar.bz2" to my desktop. What now? Ok, so I extract it.... read the readme... um "make" just make? where do I cd too? do i put something after the make command?

I guide would help, perhaps one with a virtual situation described.
thnx,
sv

---

### Post by logos34 on 2007-09-09
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Add-On_Applications](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Add-On_Applications)

---

### Post by rickycodie on 2007-09-09
also 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by steveneddy on 2007-09-09
CD to your directory that the file sits in.

make
make check
make install
make clean

Just follow the directions in the read me file that you get after you extract it, like to your desktop.

If you were DLing the file to your desktop, right click and extract here (to the desktop)

then cd to the desktop

```
cd ~/Desktop
```

then 

```
ls
```

will list the files on your desktop

cd to the folder that the file is in.

Follow the instructions in the read me file

something like

```
./configure

make

make install
```


I might be missing a step, but if you have the read me open, and you have cd to the directory, then compile away. Just follow the directions.

You may have to

sudo make
sudo make install

to get it to run right.

---

### Post by Linux_Man on 2007-09-09
You need to also make sure you have the build-essential file by doing 

sudo apt-get install build-essential because otherwise you won't be able to compile source code as ubuntu (7.04) doesn't include this by default.

---

### Post by staticvoid on 2007-09-09
Wow, thank you all so much! :)
I'll get some source code and try all this out a few times till I got it.

SV

---

