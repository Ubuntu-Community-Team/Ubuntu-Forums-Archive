---
title: "I Can't Install Anything"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Kijiro on 2006-08-19
I've tried installing several different things after installing Ubuntu on my PPC, but I can't seem to get any of them to work. Here's the terminal from the last installation I tried.
```
root@travis-laptop:/home/travis/Desktop/zinf-2.2.5# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... powerpc-unknown-linux-gnu
checking host system type... powerpc-unknown-linux-gnu
checking whether make sets $(MAKE)... (cached) no
checking for gm4... no
checking for m4... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```
I'm not sure if I'm being stupid and doing something wrong or something is just wrong with the installation.

---

### Post by Steven_B on 2006-08-19
Do you have gcc installed?  If not, do:
```
sudo apt-get install gcc
```
or use Synaptic, if you prefer.

---

### Post by meng on 2006-08-19
Yes, either that or
sudo apt-get install build-essential
which includes gcc and some other goodies for installing from source.

---

### Post by u04f061 on 2006-08-19
i think you are installing from a source package whose dependencies are not satisfied.since you seem to be new to ubuntu , you need some introduction to what are dependencies.
  these are the packages on which your programe you are trying to install depends.these dependencies are mentioned in the output you have posted
 like  hecking for gawk... no statement says that it depends on gawk .similarly other statements have this meanings.it does not mean that you need to install all the packages mentioned in the output command you posted. when linux can't find some package on which it depends ,it tries to locate an alternative. for example in the  statement

checking for gcc... no
checking for cc... no
 
gcc and cc are c compilers. first programe tried to locate gcc ,failing which it tried to locate cc. which were not installed.

one of the way to meet dependencies is that some programes comes with a file readme or manual read it first .it may have list of packages on which your programe depends.

here is another tip:
  you should have build-essential ,this is collection of some packages including c compiler which can resolve most of dependencies. you can install it this way

  sudo apt-get update
  sudo apt-get install build-essential

please mention what you are trying to install from source?
because it is not an efficient way of installation. first of all you should search in your repository like

  sudo apt-cache search <package name or description>
and then install it using

  sudo apt-get install  <package name>

---

