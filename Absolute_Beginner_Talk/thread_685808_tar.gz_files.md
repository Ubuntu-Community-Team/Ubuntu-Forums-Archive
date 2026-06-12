---
title: "tar.gz files"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2008-02-02
how does one install from a tar.gz file, i try to follow the readme in the file but how can i actually install it, is there an easy way like - copy to this file and then extract.. etc.

cheers for any/all help

---

### Post by jan quark on 2008-02-02
this will help you to get to know the different approaches to install things in ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Tenken on 2008-02-02
tar.gz files aren't install files like .debs, they are the source code for the program that you need to compile youself.[ psycocats]("http://www.psychocats.net/ubuntu/installingsoftware#other") has a nice tutorial under the installing from source heading.

---

### Post by ~LoKe on 2008-02-02
Read the file called "README" or "INSTALL"

Basically, you'd have to do...
```
./configure
make
sudo make install
```
Or...
```
./autogen.sh
./configure
make
sudo make install
```

It depends on what it contains.

---

### Post by Julita on 2008-02-02
Type in the terminal:

cd *your directory* (without asterix)
ls
tar -zxvf *filename.gz*
more INSTALL (or README; it depends on what is in the archive)

---

### Post by oldos2er on 2008-02-02
> **stubblepoo said:**
> how does one install from a tar.gz file, i try to follow the readme in the file but how can i actually install it, is there an easy way like - copy to this file and then extract.. etc.

 Depends on if the tar contains any pre-compiled binaries, or source code.
See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

