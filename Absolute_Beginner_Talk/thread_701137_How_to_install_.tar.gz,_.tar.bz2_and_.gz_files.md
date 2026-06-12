---
title: "How to install .tar.gz, .tar.bz2 and .gz files?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by v.cube on 2008-02-19
i'm not able to understand, how to install  .tar.gz, .tar.bz2 and .gz files?

Plz help:confused:

Prefferably, i want to know if it can be done without using the terminal??

---

### Post by amingv on 2008-02-19
Pretty nice read:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by PeterJS on 2008-02-19
We're going to need some more information. tar.gz, tar.bz2. and tgz, are all archive formats like zip for windows, there's really no telling what could be in there.

---

### Post by jan quark on 2008-02-19
the monkey blog says it all

tar folders are simply packed files

often there is a readme or some installation text file, which explains how to install the packed application

if you see some

configure
and 
make files

then it is very likely a source package which must be compiled

Compilation is:

Run these three commands in terminal, after you have navigate to the folder

You can navigate with 

```
cd
```

```
./configure
```

```
make
```
```

sudo make install
```
```
or
sudo check install
```

---

### Post by oedha on 2008-02-19
usually......i just double click....then extract it
next.....i have to read the readme file and install file ( the steps will be here )

---

### Post by MikeSz on 2008-02-19
Hi V.cube, I had exactly the same woe when I moved to Ubuntu a year ago.  First things first, dont panic.  Second, you need to try and forget the windows mindset that you can simply double click something and have it install - tar files are not exe's :)

As posted above, they are simply archive files - think of them as similar to a .zip or .rar

Also, the way to 'install' them will depend on what the file is and what it contains.  What are you trying to install?

---

### Post by amingv on 2008-02-19
It's also recommendable to check if the file is in the repos first, there's no point in compiling the source unless you need a newer development version or it's not in the repos (or the one in the repos is too outdated).

> **MikeSz said:**
> [...]dont panic[...]

I like that phrase, it should be on every guide...:)

---

### Post by MikeSz on 2008-02-19
> **amingv said:**
> It's also recommendable to check if the file is in the repos first, there's no point in compiling the source unless you need a newer development version or it's not in the repos (or the one in the repos is too outdated).



I like that phrase, it should be on every guide...:)

I have to admit robbing that from a certain Mr Douglas Adams....

---

### Post by hyper_ch on 2008-02-19
Are you sure that you cannot find the programs in the repositories?

---

### Post by amingv on 2008-02-19
> **MikeSz said:**
> I have to admit robbing that from a certain Mr Douglas Adams....

I know, but you missed the big friendly letters.

---

### Post by jan quark on 2008-02-19
what are you trying to install?

perhaps this package is in the synaptic repositories as hyper mentioned above

or there is a .deb package of this application which can be installed by double-clicking like an exe

if you tell us, we might help

---

### Post by talsemgeest on 2008-02-19
Simply extract it onto the desktop and tell us what it contains

---

### Post by johnfarrow on 2008-02-29
procedure for installing LightZone-3.4.tar.gz

---

### Post by PeterJS on 2008-02-29
> **johnfarrow said:**
> procedure for installing LightZone-3.4.tar.gz

Are you really still running Breezy? If so upgrading to something less ancient wouldn't hurt.

Barring that have you read the README or INSTALL file? could you link to where you got that from so we can read the instructions.

As was discussed at the beginning of this thread, tar.gz is just an archive format, so we can offer some reasonable guess as what's probably in it, but it's just a guess.

---

### Post by KDE_rocks2345 on 2008-04-04
> **jan quark said:**
> the monkey blog says it all

tar folders are simply packed files

often there is a readme or some installation text file, which explains how to install the packed application

if you see some

configure
and 
make files

then it is very likely a source package which must be compiled

Compilation is:

Run these three commands in terminal, after you have navigate to the folder

You can navigate with 

```
cd
```

```
./configure
```

```
make
```
```

sudo make install
```
```
or
sudo check install
```

Your instructions don't work for me :confused:

---

### Post by talsemgeest on 2008-04-04
cd is just like double-clicking on a folder in nautilus. For example, to go to your desktop, you would type: ```
cd ~/Desktop
```

---

