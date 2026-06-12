---
title: "Ubuntu 7.04 comes with GCC compiler or not."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-01
I can't install multimedia codecs and drivers with the usual comand ./configure---make---make install

It tells me that gcc is not runing.

Iinstalled ubuntu 7.04 with a Live cd.

what should i do in these conditions ?

---

### Post by hyper_ch on 2007-10-01
```

sudo apt-get install build-essential

```

---

### Post by lynxus on 2007-10-01
I really think build-essential should be installed by default. 

Maybe its just me, But hummm

---

### Post by hyper_ch on 2007-10-01
why should it be installed by default?

---

### Post by cmnorton on 2007-10-01
One of the complaints about many Linux distributions, not necessarily Ubuntu, is that the distros are "bloatware". Everything gets installed, or it seems like everything. Perhaps the Ubuntu install could prompt for the kind of installation to pre-install widely downloaded packages. But then, I do not know if that breaks the simple install spirit of Ubuntu.

---

### Post by dptxp on 2007-10-01
> **lynxus said:**
> I really think build-essential should be installed by default. 

Maybe its just me, But hummm

1) A  CD can store 700 MB data.

2) One of the reasons why I do not like KDE because it has too many items on Menu

---

### Post by bambubambu2 on 2007-10-01
Damn,i can't make him work!

i nsserted the line and look what cames out:

root@zzz-desktop:  sudo apt-get install build essential
Reading package lists........Done.
Building dependency tree 
Reading state information... Done.
E. couldn't find pakage build essential

Any ideea????

What should i do for compiling ???

---

### Post by ruibernardo on 2007-10-01
You forgot the hifen. It is "build-essential"!

---

### Post by bambubambu2 on 2007-10-01
No i 'd copy and pasted             sudo apt-get install build-essential

What i wrote lately was from memory


I'm definetly sure that i wrote corectly.

But you ,users of Ubuntu 7.04 installd with an live cd, you can use il gcc compiler or is realy missing from the live cd eddition.

Maybe there in an install cd with gcc and oher programs.
Mabye this is a demonstrative version????????

help

---

### Post by ruibernardo on 2007-10-01
If you don't have a internet connection to use the repositories, then use the Alternate CD (download needed). 

The Desktop CD (LiveCD) doesn't allow you to install any package from it, it just runs and installs Ubuntu. 

The Alternate CD does have the packages available (like a repository) and you can install packages from that CD, or if you boot from it, install Ubuntu without a GUI, but you can't run Ubuntu from that CD. 

The package build-essential is on the Alternate CD.

---

### Post by hyper_ch on 2007-10-01
the alternate cd does allow to install packages ;)

---

