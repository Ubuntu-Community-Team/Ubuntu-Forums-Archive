---
title: "Tarball usage"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by K_Alex on 2007-05-23
I sorta understand what a tarball is (superzipped files for a program) but could someone please explain to me how to turn tar into a shiny program, plugin etc..

---

### Post by Sparkster185 on 2007-05-23
A tar file is a group of files/directories combined into one file (tar stands for tape archive).  a "tarball" is a tar file that has been compressed, usually with gzip, so the extension is ".tar.gz"

To uncompress the file myTarball.tar.gz you would type

```
tar -xvfz myTarball.tar.gz
```

The -x means "eXtract", the -v means "verbose" (lists the files that come out, and this is optional), the -f means that you are going to specify a File, and the -z means that it's a zipped file.

Once you untar the file, you should find a README, or some instructions.

---

### Post by vtel57 on 2007-05-23
GOOGLE is your friend... get to know it. ;)

[http://berkshirelug.org/mediawiki/index.php/InstallTarball](http://berkshirelug.org/mediawiki/index.php/InstallTarball)

---

