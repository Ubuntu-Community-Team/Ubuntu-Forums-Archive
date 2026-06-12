---
title: "tar.gz file games"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-07-02
How in the world do you install games that are .tar.gz. I don't know how. Still a ubuntu noob.

---

### Post by RomeReactor on 2007-07-02
Hi. **.tar.gz** files are compressed file formats, like zip or rar; try double-clicking on the file to bring up File Roller, the archiver/unarchiver, and extract its contents; inside there should be at least one file named README or INSTALL, which will tell you how to proceed with the installation, most likely with commands to be issued from the terminal (Applications->Accessories->Terminal).

---

### Post by KIAaze on 2007-07-02
The quick answer:
```
tar -xzvf game.tar.gz
cd game
./configure
make
sudo make install

```

Et voilà! :)

And just so you understand what you are doing:

1)tar -xzvf game.tar.gz -> extract files from the tar.gz file: x=extract, z=gzipped file, v=verbosely, f=file (use "j" instead of "z" case of tar.bz2 files) (you can also extract by right-click->extract here)

2)cd game -> change to the newly created directory

3)./configure ->check for dependencies and create the Makefile needed by the make command
If you want to install in a specific directory (default is usually "/usr/local"), you can use ./configure --prefix=/home/login/thegame for example.

4)make -> Compile the program

5)sudo make install -> install it (i.e: put the files in the right directories with the right permissions)

edit:
Yeah, as said in the previous post, you should read the Readme and Install files.
The method I gave is the most common one, but sometimes it can be different.

---

### Post by buzzmandt on 2007-07-02
computer-geek, what's up with all the for free pm me?
you did the same thing in another thread for crossover

---

### Post by Istonian on 2007-07-02
Thanks for your help. I now have the game running.

---

### Post by RomeReactor on 2007-07-02
**Istonian**, glad to hear you got it working!

**Computer-Geek**, please refrain from posting comments like that; [Crossover Office]("http://www.codeweavers.com/products/cxoffice/") is a  proprietary program and is not free, you have to pay to use it. [Cedega]("http://www.transgaming.com/products/cedega/") does offer the option of downloading the [source code for free]("http://winecvs.linux-gamers.net/index.php/Main_Page"), so you can compile it and use it. However, they don't offer support for that version, only for a paid subscription, and you must update it manually (by downloading and recompiling).

---

