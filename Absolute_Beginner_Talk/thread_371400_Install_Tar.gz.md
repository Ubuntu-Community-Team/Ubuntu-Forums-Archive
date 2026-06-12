---
title: "Install Tar.gz"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-02-26
Hi:
I am trying to install a tar.gz file.  I found the "install anything in Ubuntu site.  I've installed build-essential using synaptic.  I can extract the file.  I can navigate to the directory in terminal.  When I try to ./configure, I get  bash: ./configure: No such file or directory

I notice that there is no .configure folder, yet build-essential seemed to install ok.  What do I do?

Thanks,
Ziffnabb

---

### Post by taurus on 2007-02-26
While in the newly directory that you have extracted, what's the output of this command?

```
ls -la
```
What are you trying to build from source anyway?

---

### Post by aysiu on 2007-02-26
Can you mention the name of the program you're trying to install? Not all .tar.gz files are the same. Firefox, for example, is a precompiled binary.

---

### Post by bodhi.zazen on 2007-02-26
It usually helps to read the README file ;)

---

### Post by ziffnabb on 2007-02-27
The output of ls -la is:

drwxr-xr-x  3 bruce bruce     4096 2007-02-26 21:19 .
drwxr-xr-x 52 bruce bruce     4096 2007-02-27 17:56 ..
-rw-r--r--  1 bruce bruce 77257508 2007-02-26 20:33 scourge-0.17.data.tar.gz
drwxr-xr-x 15 bruce bruce     4096 2007-02-26 20:35 scourge_data
-rw-r--r--  1 bruce bruce   584807 2007-02-26 20:33 zaxrr.wip.0.4.125.tgz


It is called Scourge, and it is a game (if you have not already guessed).

There was no readme file.

Thanks,
Ziffnabb

---

### Post by Maestro23 on 2007-02-27
> It is called Scourge, and it is a game (if you have not already guessed).

There was no readme file.

Thanks,
Ziffnabb

Is this the game?: [http://linux.strangegamer.com/index.php?title=S.C.O.U.R.G.E](http://linux.strangegamer.com/index.php?title=S.C.O.U.R.G.E).

From the INSTALL doc:

> # To check out the code and data into a scourge directory
svn co [https://svn.sourceforge.net/svnroot/scourge/trunk](https://svn.sourceforge.net/svnroot/scourge/trunk) scourge

# To configure it
cd scourge/scourge
autoreconf -i

# To compile it
cd ..
mkdir build
cd build
../scourge/configure --enable-debug
make

# Run
./src/scourge -f

Thanks,
--Gabor
(cctorok@yahoo.com)


There is also a README file in the extracted directory as well.

---

