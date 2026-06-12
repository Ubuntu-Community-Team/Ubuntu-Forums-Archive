---
title: "Manual Installs"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by JDavid5381 on 2006-03-17
Does anybody no of a good online guide for Linux beginners on installing software manually using the BASH command line?  I'm new to Linux and Ubuntu and have just begun learning how to install things by running "sudo apt-get," on the CLI (Terminal), but I have some linux programs that I want installed which aren't included in the Universe or Multiverse repositories of apt-get.  Any help would be great.  Thanks in advance.

-James

---

### Post by bjweeks on 2006-03-17
Read the 'readme' and 'install' files in the tarball.

---

### Post by 5-HT on 2006-03-17
Are you referring to compiling apps?

Here's a wiki link on the topic:
[https://wiki.ubuntu.com/CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware")

Also, 'checkinstall' is a nice utility that lets you make and install a .deb out of the source (sort of). 
Instead of 'make install' just use 'checkinstall' and if all goes well, the app will be much easier to remove (just via dpkg/apt/synaptic/aptitude....).

Here's a wiki link on 'checkinstall':
[https://wiki.ubuntu.com/CheckInstall]("https://wiki.ubuntu.com/CheckInstall")

HTH

---

### Post by taurus on 2006-03-17
Usually, the source file comes in tar.gz or tar.bz so you have to uncompress and untar it!!!  For instance, if you download something that looks like file.tar.gz (or even file.tgz), then you would run this to unpack it,
```

tar xvzf file.tar.gz

```
But if it looks like file.tar.bz (or file.tbz), then you would run
```

tar xvjf file.tar.bz

```
Then, you will see a new directory called file so change to there with the cd command and read either README or INSTALL but mostly likely, you need to do something like these to install it,
```

cd file
./configure
make
sudo make install

```

---

