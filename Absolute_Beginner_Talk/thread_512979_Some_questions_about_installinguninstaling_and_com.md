---
title: "Some questions about installing/uninstaling and compiling"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by tico on 2007-07-30
Hi,

I'd like to know:

1. how to install/uninstall packs (tarball or deb packs) in terminal?
2. what exactly is "compile" and how/why I do this?

A real case:

I've uninstalled the Openoffice distro that comes with Ubuntu and installed the official one (28 deb packs converted with alien from rpms). I had to install one by one. Is there a way to install all these packs with just one command? How? And what about uninstalling it?

Thanks.

---

### Post by FleetAdmiral74 on 2007-07-30
What do you mean...I am using the unofficial open office right now? Just install if from the repos, best method IMO. it keeps track of all those dependencies for you, and to be honest I have no clue why you installed it from the RPMs...

1) [http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/](http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/)

2) I am no expert, but compiling is what you do to the code to..make it executable on your system, I think. This will explain it better then I can, [http://en.wikipedia.org/wiki/Compiler](http://en.wikipedia.org/wiki/Compiler)

---

### Post by tico on 2007-07-30
The Openoffice that comes with Ubuntu was giving me some troubles with some foreign characters. Unistalling it and installing the official Openoffice (i. e. the one that you can find in the Openoffice site) solved this issue.

---

### Post by pyros on 2007-07-30
> **tico said:**
> 
1. how to install/uninstall packs (tarball or deb packs) in terminal?

to install a tarball, first you will need to install the build-essential package from the repositories:
untar the tarball, go into the source directory and type:
```

./configure
make && make install

```
to uninstall a tarball:
untar the tarball, open a terminal, go into the source directory and type:
```

./configure
make && make uninstall

```
to install a deb:
open a terminal and type
```

sudo apt-get install PACKAGENAME

```
to uninstall a deb:
open a terminal and type
```

sudo apt-get remove PACKAGENAME

```
> **tico said:**
> 
2. what exactly is "compile" and how/why I do this?

Compiling, simply put, is converting a set of instructions from a format that is relatively easy for humans to understand into a format that the computer can understand.

---

### Post by tico on 2007-07-30
Thanks for helping.

And in the case that I have 28 deb packs in my hard drive (the official Openoffice), how could I install them with a few commands and uninstall?

---

### Post by pyros on 2007-08-01
> **tico said:**
> Thanks for helping.

And in the case that I have 28 deb packs in my hard drive (the official Openoffice), how could I install them with a few commands and uninstall?

I *think* you could do this with the command 
> 
sudo dpkg -i *.deb 

in the directory of the packages you have.

---

### Post by Sk1ppy on 2007-08-01
> **pyros said:**
> ...go into the source directory...

How do you go into the directory with the terminal?

---

### Post by splintercellguy on 2007-08-01
cd "whatever the directory is"

---

### Post by Sk1ppy on 2007-08-01
Now when I'm in the directory and type "make" after i do the "./configure" it says ```
make: *** No targets specified and no makefile found.  Stop.
```
What does this mean? (I'm trying to install Pidgin 2.1.0)

---

### Post by imspecial on 2007-08-01
> **Sk1ppy said:**
> Now when I'm in the directory and type "make" after i do the "./configure" it says ```
make: *** No targets specified and no makefile found.  Stop.
```
What does this mean? (I'm trying to install Pidgin 2.1.0)

did you get any error messages when running ./configure?


for uninstalling I believe you could remove it with 

```

sudo apt-get remove packagename

```
as once you install a .deb it is indexed by apt and can be uninstalled through synaptic, so I am assuming you can remove it through apt.

---

### Post by pyros on 2007-08-01
> **Sk1ppy said:**
> Now when I'm in the directory and type "make" after i do the "./configure" it says ```
make: *** No targets specified and no makefile found.  Stop.
```
What does this mean? (I'm trying to install Pidgin 2.1.0)

try typing 
```

ls > ls.txt

```
in the directory where you are trying to run make, that should create an ls.txt file in that directory, and attach it to your reply.

---

### Post by Sk1ppy on 2007-08-01
> **imspecial said:**
> did you get any error messages when running ./configure?.

Yeah I did lemme find it:

```
configure: error: C compiler cannot create executables
```

And I attached the .txt file pyros wanted.

---

### Post by Sk1ppy on 2007-08-01
umm... bump?

---

### Post by pyros on 2007-08-02
I'm afraid you have me at a loss. The only thing I could recommend is using the pidgin 2.1 deb from getdeb:
[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

