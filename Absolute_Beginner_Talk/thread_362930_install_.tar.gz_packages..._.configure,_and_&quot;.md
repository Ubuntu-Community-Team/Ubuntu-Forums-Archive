---
title: "install .tar.gz packages... ./configure, and &quot;make&quot; don't work..."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-02-16
I'm using Kubuntu Dapper, and I've tried the ./configure thing, and also the "make" command, and the system doesn't even recognize those commands.
What should I do for the system to recognize the "make" thing?
and
What do I do to install my .tar.gz packages I just downloaded?
My Adept doesn't seem to find them.

---

### Post by hanexar on 2007-02-16
you need to install the package for the compiling tools:

```
sudo apt-get install build-essential
```

I suggest you give a look at this page:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ComplexNumber on 2007-02-16
> **aalr1986 said:**
> I'm using Kubuntu Dapper, and I've tried the ./configure thing, and also the "make" command, and the system doesn't even recognize those commands.
What should I do for the system to recognize the "make" thing?
and
What do I do to install my .tar.gz packages I just downloaded?
My Adept doesn't seem to find them.
have you got a link to where you downloaded it from so i can have a look at the package concerned? i'm thinking that maybe it doesn't have a configure script.

---

### Post by bodhi.zazen on 2007-02-16
First of all, try to install from the repositories if possible. The repo's are quite large ...

How to enable repositories : [http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

OK, next you need to extract the archive and see if there is a README file.

Not all archives are equal, some packages are distributed as source code, others as python scripts, and others as binaries ...

hanexar 's advice is good if you need to compile as ...

You may also want to look at checkinstall 

Checkinstall does not always work, but if it does it makes updating or uninstalling easier :)

Last, take a look at this :

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by konungursvia on 2007-03-03
> **aalr1986 said:**
> I'm using Kubuntu Dapper, and I've tried the ./configure thing, and also the "make" command, and the system doesn't even recognize those commands.
What should I do for the system to recognize the "make" thing?
and
What do I do to install my .tar.gz packages I just downloaded?
My Adept doesn't seem to find them.

Also, instead of ./configure, you can look for a file with the .binary extension among the unpacked files from your tarball. One of these is often executable and you just need to type 
./nameofbinaryfile instead of ./config to get a number of tarball packages to install themselves after unpacking.

---

