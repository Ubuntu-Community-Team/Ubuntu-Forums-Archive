---
title: "gcc-3.4.6.tar.gz enough for compiling programs ?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-15
i use ubuntu  7.04 without internet connexion.
I really tried everithing but seems that are missing a lot of dependencies.
I search on GNU GCC site and i found this archive of 40 mega.:gcc-4.2.2.tar.bz2

if i will download it i will be ok ? Or i will have to download other libreries?
tHERE IS A PRECOMPILED VERSION OF THE GCC FOR UBUNTU?


really the lack of gcc is such a mess.Now i know why linux is such unpopular

---

### Post by LaRoza on 2007-10-15
```
sudo aptitude install build-essential
```

It is on the CD, but not installed (which bugs me).

gcc itself is installed, but build-essential has everything you'll need for compiling C and C++ programs.

Linux is popular with users who don't need their hands held, or who can at least use google and other search features to find answers to simple questions.

The tarball you downloaded probably has a READ ME explaining how to use it.

---

### Post by bambubambu2 on 2007-10-15
> **LaRoza said:**
> ```
sudo aptitude install build-essential
```

It is on the CD, but not installed (which bugs me).

gcc itself is installed, but build-essential has everything you'll need for compiling C and C++ programs.

Linux is popular with users who don't need their hands held, or who can at least use google and other search features to find answers to simple questions. (Look in the programming talk forum)

The tarball you downloaded probably has a READ ME explaining how to use it.


no , like i said i allready did sudo apt-get install build-essential.i
i installed build essential from the live cd with synaptic manager.

The problem comes out when i try to ./configure mulrimedia plugins or vlc media player or even a DOSEMU
Something is missing aniway.

i TRY very hard to solve this but seems that nowone can do it without a internet connexion wich bugs me.

---

### Post by LaRoza on 2007-10-15
What error messages are you getting?

I don't have an internet connection either, and use repository DVD's, from thelinuxstore.ca

(My address, 169.254.171.208 is an address that only computers not connected to the internet have)

---

### Post by bambubambu2 on 2007-10-15
error such : missing lex or flex,

like the current file is older that existing....or something.

what shoudl i do ?

Clearly gcc dosn't work
wHAT FILE SHOULD I DOWNLOAD AND INSTALL?

 this archive of 40 mega.:gcc-4.2.2.tar.bz2 IS OK ?

---

### Post by az on 2007-10-15
> **bambubambu2 said:**
> error such : missing lex or flex,

like the current file is older that existing....or something.

what shoudl i do ?

Clearly gcc dosn't work
wHAT FILE SHOULD I DOWNLOAD AND INSTALL?

 this archive of 40 mega.:gcc-4.2.2.tar.bz2 IS OK ?

You don't need gcc - it's telling you you need flex.  ([http://packages.ubuntu.com/feisty/devel/flex](http://packages.ubuntu.com/feisty/devel/flex))

---

### Post by Paul820 on 2007-10-15
Are you sure you have all the dependencies for the programs you are trying to install. If you don't have access to the internet then you might not have everything that the program you are trying to compile requires. There are so many more things you need to build programs than just build-essential, a lot of programs depend on gtk, sdl, opengl, wxwidgets, libcairo and the list goes on. Most of those can only be downloaded from the internet. Have a look at the README file inside the archive of the program you are trying to compile like LaRoza said, or have a look at the INSTALL file and see what is required to build it.

---

