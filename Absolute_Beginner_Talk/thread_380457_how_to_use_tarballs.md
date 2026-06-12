---
title: "how to use tarballs??"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gamer91 on 2007-03-09
can anyone help me - I need to know how I install a program from a tar file - im very confused

---

### Post by taurus on 2007-03-09
Section 4.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Or

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by r4ik on 2007-03-09
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

good luck !

---

### Post by lamalex on 2007-03-09
tar -xvf yourfile.tar from command line. then go inside of it and do what the readme or install file says to do!

---

### Post by gamer91 on 2007-03-09
it says that "xrender" was not found - what does this mean?

---

### Post by undertakingyou on 2007-03-09
Probably a dependecy . . .  try ```
sudo apt-get install xrender
```

---

### Post by invalid on 2007-03-09
> **gamer91 said:**
> it says that "xrender" was not found - what does this mean?

You may be in the wrong directory. If you downloaded it from firefox, typically it will end up on your desktop. Try```
cd ~/Desktop
```to change your directory.```
ls
```will show you the files in your current directory.

---

### Post by gamer91 on 2007-03-10
still having problems - i'll give you what terminal says:

>  checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:

No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS
and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


---

### Post by gawdin on 2008-03-11
imagine that, I am having the same problem...

apt-get install xrender says the package is not found

I am getting this error while trying to ./configure the beryl-core program

---

### Post by VoidedCheck on 2008-03-11
If you're compiling from source and it has a dependancy, you need to install the development package of the dependancy in question, in this case I think it's

```
sudo apt-get install libxrender-dev
```

---

### Post by Oldsoldier2003 on 2008-03-11
> **VoidedCheck said:**
> If you're compiling from source and it has a dependancy, you need to install the development package of the dependancy in question, in this case I think it's

```
sudo apt-get install libxrender-dev
```
```

sudo apt-get build-dep <package_you_are_ trying_ to_ build>
```
usually works as well

---

### Post by VoidedCheck on 2008-03-11
Oh, neat.  Thanks, that makes things much easier.

---

