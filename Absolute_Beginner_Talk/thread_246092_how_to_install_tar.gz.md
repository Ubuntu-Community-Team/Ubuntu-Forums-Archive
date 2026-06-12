---
title: "how to install tar.gz?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-08-28
So I know how to use deb files and add the aptitude install thingy but how do I install a program I downloaded as tar.gz?

---

### Post by Anonii on 2006-08-28
.tar.gz is a compressed folder. Like .zip and .rar in Windows.
You can simply extract them in another folder either by running:
*tar xvf <filename>.tar.gz* in the console, or by opening them with an archive manager, like "File Roller" or "ark" which your system will probably allready have installed. You just have to double-click the archive and then extract it by drag and dropping the files/folders somewhere.
Also, about the tar command. You want to use "man tar" to learn more options, since there are many ways to extract a .tar.gz archive.

---

### Post by Bachstelze on 2006-08-28
Software in tarballs are most of the time source code you'll have to compile yourself to get the soft working. If you're a beginner, this might be a tough process. What is it you are trying to install ?

---

### Post by bodhi.zazen on 2006-08-28
Extract as above

cd name-of-program

READ README
```
./configure
make
sudo make install
```

consider using checkinstall rather then make install.

You will need to install checkinstall first; check install does not always work.

```

sudo apt-get install checkinstall
./configure
make
sudo checkinstall
```

[http://ubuntuforums.org/archive/index.php/t-2356.html](http://ubuntuforums.org/archive/index.php/t-2356.html)

(look at the first post)

You may need to install linux-headers, make, gcc, and other packages. It is up to you to resolve dependencies.

---

### Post by Bachstelze on 2006-08-28
> **bodhi.zazen said:**
> 
You may need to install make, gcc, and other packages. It is up to you to resolve dependencies.

That's what **build-essential** is for ;)

---

### Post by bodhi.zazen on 2006-08-28
> **HymnToLife said:**
> That's what **build-essential** is for ;)

Oh.. I had no Idea. I am doing it the hard way I see.

THANK YOU

---

### Post by xyz on 2006-08-28
Also...this link helped me:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ~zoey~ on 2006-08-29
I am trying to install a tarball.  I get to ./configure and get the message'no such file or directory' as ~ and 'command not found as root.  I have installed gcc, debian configure, build-essential, and make was already installed.  I have installed tarballs before, but I am stuck.  What should my next move be?

I am running Dapper and the tarball is checkbook tracker.

The readme file just says that it is an ELF executable file, and I have googled, but can't find any installation instructions.

Thanks, zoey](*,) :confused: ](*,)

---

### Post by helloamit83 on 2006-09-02
can anybody tell me how to intall vmd and namd .. m not able to insatall .. it say . 
make: *** No rule to make target `install'.  Stop.

plzz help](*,) ](*,)

---

### Post by aranal blues on 2007-07-07
> **helloamit83 said:**
> can anybody tell me how to intall vmd and namd .. m not able to insatall .. it say . 
make: *** No rule to make target `install'.  Stop.

plzz help](*,) ](*,)
I got the same problem, can anyone help?

---

### Post by LIEFofEeofol on 2007-12-25
> **~zoey~ said:**
> I am trying to install a tarball.  I get to ./configure and get the message'no such file or directory' as ~ and 'command not found as root.  I have installed gcc, debian configure, build-essential, and make was already installed.  I have installed tarballs before, but I am stuck.  What should my next move be?

Thanks, zoey](*,) :confused: ](*,)

you have to extract the .tar.gz first, then ./configure in the new directory

---

