---
title: "Installing a .tgz"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by wishipu on 2007-12-17
I am having a hard time trying to install "Audicle". The "Read me" and the "Installation" files have either instructions. And the "cd, ./configure, make..." commands doesn't work...

---

### Post by jken146 on 2007-12-17
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Sef on 2007-12-17
> And the "cd, ./configure, make..." commands doesn't work.

Have you installed build-essential?  Without it, ./configure, make will not work.

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by wishipu on 2007-12-18
Still something is wrong.

sorenlorenson@wishipu:~$ cd '/home/sorenlorenson/Desktop/audicle-1.0.0.6'
sorenlorenson@wishipu:~/Desktop/audicle-1.0.0.6$ ./configure
bash: ./configure: No such file or directory
sorenlorenson@wishipu:~/Desktop/audicle-1.0.0.6$

---

### Post by nowshining on 2007-12-18
cd into the source directory usually named src and also

it's 

./configure

make

sudo make install

sudo make clean to remove tmp files

if u want and checkinstall is installed u can easiily build a deb file

then the command would go

./configure

make

sudo checkinstall -D make install

answer the questions and change what ever u want, add a description and more.

then

sudo make clean

then

go into the directory of the program unzipped / untared

find the program's deb file and copy it somewhere else, it's owned by root so u'll need to change the permissions if'd u'd like to move it but copying should work fine.

---

### Post by mozetti on 2007-12-18
I just looked at the instructions. It doesn't say anything about running ./config.

-- Unpack the tgz file. ```
tar -xvf audicle-1.0.0.6.tgz
```
-- cd into the "audicle-x.x.x.x/src/" directory ```
cd audicle-1.0.0.6/src
```
-- Run make linux-oss, make linux-alsa, or make linux-jack, depending on the sound system you're using (most likely alsa). ```
make linux-alsa
```
--Run make install ```
make install
```
--Run audicle ```
audicle
```

*Note* - you may need to use "sudo" before your "make linux-alsa" and "make install"

It's not really that difficult if you just read the instructions on the website.

---

### Post by wishipu on 2007-12-19
Thank you very much!!! that work very well.

Now I am ready to try this software.

---

