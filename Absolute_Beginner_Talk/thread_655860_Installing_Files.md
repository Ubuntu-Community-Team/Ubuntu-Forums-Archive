---
title: "Installing Files"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by lkirlin on 2008-01-01
Hi, I am having trouble with a docking application: 
after un-taring the file, I get this message:

```
kirlin@kirlin-desktop:~$ sudo apt-get install /home/kirlin/Desktop/simdock_1.2.tar.gz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 
kirlin@kirlin-desktop:~$ 

```

How do i properly install this file and/or properly un-tar it?

---

### Post by kevdog on 2008-01-01
I dont know, but Im betting the contents of that file you are trying to install are likely source code and you will need to compile it.

To untar the file its:

tar -zxvf <filename>

Likely its going to be source code rather than an executable.  I could be wrong.

---

### Post by Shazaam on 2008-01-01
This will help with installing stuff....

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by SOULRiDER on 2008-01-01
I suggest you read [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) its important that you learn the basics of how package management works before trying to install somehting. Check it out and ask anything you dont understand, we will gladly help.

---

### Post by thelatinist on 2008-01-01
Everything everyone has said above is true. It looks to me, though, like you are trying to build something from source and install it.  While it is almost always better to install a package from the repositories, if you do need to install something that isn't in the repositories, do the following:

```
sudo mkdir ~/src
sudo mkdir ~/src/simdock_1.2
cd ~/src/simdock_1.2
tar xvfz ~/Desktop/simdock_1.2.tar.gz
./configure
make
make install
make clean
```

To explain these commands:

**sudo mkdir ~/src** creates a folder in your home directory to hold the source files for all programs you may install from source.  You only need to do this the first time you install something from source.
**sudo mkdir ~/src/simdock_1.2** creates a directory to hold the source files for *this* program.
**cd ~/src/simdock_1.2** switches to the directory you just created
**tar xvfz ~/Desktop/simdock_1.2.tar.gz** untars the file from your desktop to the folder you are currently in.
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean **removes configuration files from the current directory.

---

### Post by SOULRiDER on 2008-01-02
Instead of make install its better to do a checkinstall. That will create a deb package that is easy to remove.

---

### Post by thelatinist on 2008-01-02
> **SOULRiDER said:**
> Instead of make install its better to do a checkinstall. That will create a deb package that is easy to remove.

Thanks for the advice.

---

