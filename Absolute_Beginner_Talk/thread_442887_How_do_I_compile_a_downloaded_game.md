---
title: "How do I compile a downloaded game?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by original_jamingrit on 2007-05-14
I've been using Ubuntu for a while, but I still feel like a newbie.  I kind of know what I'm supposed to do here, but I'm not sure how to get started.  I've been wanting to know how to do this for a few other programs as well.

I downloaded the tarball for the game, OpenArena, available at [http://openarena.ws/?files]("http://openarena.ws/?files").  It has in the archive some binaries(*i386* and *x86_64*), and the source code as well.  I want to know how/where to compile the source code and make the game playable.  I've already got build-essential, and the OpenArena source files includes a makefile (which I'm not sure how to use), and I just need to know what to do next.

I know it may just something as simple as making the binaries executable or something like that, but I'd like to know how to compile the source code.  Any advice, suggestions, or even step-by-step instructions would be greatly appreciated, especially from anyone who has installed OpenArena before.

---

### Post by bobplano on 2007-05-14
since you already have build-essential you just need to make it. go to the directory in the terminal (cd) and then type```
make 
sudo make install
```
then the game should be running. if there is a configure file you might want to run
```
./configure
``` before using make

---

### Post by lamalex on 2007-05-14
if theres a make file try just typing. Also look for a configure.sh or similar script and run that:
```

./configure
make
sudo make install

```
also look inside your folder for a README or INSTALL file.

---

### Post by original_jamingrit on 2007-05-14
I just found out that this game is in the offical repository starting with Feisty, but I'd still like to know the procedure for installing a game from source code.

---

### Post by original_jamingrit on 2007-05-14
Got it.  That was easier than I thought.  Thanks guys =-)

---

