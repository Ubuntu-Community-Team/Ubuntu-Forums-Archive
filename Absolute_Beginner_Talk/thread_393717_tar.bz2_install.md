---
title: "tar.bz2 install???"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by MrSoxs on 2007-03-26
Hi Guys, 

Was wondering how in Edgy you install tar.bz2 files.  I know it has to be extracted but im not sure on the compiling process or what todo next???

Can anyone help me?

Cheers:confused:

---

### Post by Koybe on 2007-03-26
First, untar your file  :

```
tar xjf /path/to/your/file -C /destination/path
```Then most of the time compiling consist of 
```
./configure
make
sudo make install

```But it depends on the program you want to install. You should find a README after extracting the files.

Don't forget to get the build-essential package before compiling :
```
sudo apt-get install build-essential
```

---

### Post by zvacet on 2007-03-26
tar jxvf program.tar.bz2
You will see folder so 
cd /program
and compile
1. ./configure
2. make
3. sudo make install

---

### Post by aysiu on 2007-03-26
Is it something you are unable to find in the repositories?
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I've never found the need to compile an application from source.

---

### Post by cowlip on 2007-03-26
Are you trying to install something that's not in the repositories (have you checked all of them, universe, multiverse, debian repos?) or that doesn't have a .deb file?  If so, after it has been extracted with:

tar -zxvpf myfile.tar.gz

you will probably end up with some configure files.  Also, read the README file.  In Edgy, you have to install a package called 'build-essential' first, but this is included by default in the next version called feisty fawn.  Anyways, compile it with

sudo apt-get install build-essential.

Then, the steps are:

1) ./configure (if any errors come up, it's likely due to dependancies that you have to install)

2) make

3) sudo make install

In ubuntu, it's usually better to replace 'sudo make install' with a program called 'checkinstall' so you can manage it in Synaptic or install it on other systems quickly, which you should install beforehand with:

sudo apt-get install checkinstall 

That will create a .deb package which you can double click or install with 

sudo dpkg -i PACKAGENAME

---

### Post by seshomaru samma on 2007-03-26
it's probably best to read this :
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

---

### Post by cowlip on 2007-03-26
> **seshomaru samma said:**
> it's probably best to read this :
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

I have to say, that's a really nice walkthrough :)

---

### Post by aysiu on 2007-03-26
> **cowlip said:**
> I have to say, that's a really nice walkthrough :)
It's also just a mirror for this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

