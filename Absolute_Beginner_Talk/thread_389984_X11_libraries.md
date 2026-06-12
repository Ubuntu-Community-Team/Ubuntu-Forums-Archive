---
title: "X11 libraries"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-03-21
Right I have finally managed to download Ubuntu and now while trying to install/compile FLTK 1.1.7 I get an error when I enter the command 'MAKE' it scrolls throu a load of stuff then comes up with this:-
checking for X... no
configure: error: Configure could not find required X11 libraries
./configure: line 10022: exit: aborting.: numeric argument required
./configure: line 10022: exit: aborting.: numeric argument required
make: *** [makeinclude] Error 255


So how do I go about getting the required X11 libraries??

Any ideas?
Ian

---

### Post by yabbadabbadont on 2007-03-21
sudo apt-get build-dep libfltk1.1

You might also consider installing xorg-dev if you haven't already.

---

### Post by yabbadabbadont on 2007-03-21
Just out of curiosity, why are you building it from source?  It is in the repositories.
```
/home/bubba $ aptitude show libfltk1.1
Package: libfltk1.1
State: not installed
Version: 1.1.7-2
Priority: optional
Section: libs
Maintainer: Aaron M. Ucko <ucko@debian.org>
Uncompressed Size: 864k
Depends: libc6 (>= 2.4-1), libgcc1 (>= 1:4.1.0), libgl1-mesa | libgl1, libglu1-mesa | libglu1, libjpeg62, libpng12-0 (>=
         1.2.8rel), libstdc++6 (>= 4.1.0), libx11-6, libxext6, libxft2 (> 2.1.1), libxinerama1, zlib1g (>= 1:1.2.1)
Conflicts: libfltk1.1c102
Replaces: libfltk1.1c102
Description: Fast Light Toolkit shared libraries
 Libfltk1.1 contains the files necessary for running programs dynamically linked with FLTK, a very nice LGPLed cross-platform
 graphical user interface toolkit originally based on libForms. 
 
 URL: http://www.fltk.org/

```

---

### Post by ianb72 on 2007-03-21
> **yabbadabbadont said:**
> 
You might also consider installing xorg-dev if you haven't already.

Cheers,
Is that sudo apt-get build-dep xorg-dev??

I am just making the switch from Windoze and its taking a bit of time getting used to all of this, but I'll get the hang of it and it seems so much faster even on this old 800Mhz pc than Windoze XP Pro on my 3Ghz pc :) 

Yet again thanks
Ian

---

### Post by ianb72 on 2007-03-21
> **yabbadabbadont said:**
> Just out of curiosity, why are you building it from source?  It is in the repositories.


Iam just following the instruction for installing Fldigig with fltk 1.1.7 and I may have to use hamlib too, but as I said I am finding it all a bit nerve racking at the mo!!

Ian

---

### Post by yabbadabbadont on 2007-03-21
> **ianb72 said:**
> Cheers,
Is that sudo apt-get build-dep xorg-dev??


No, you only use build-dep if you wish to install the build dependencies for the named package.  You use "sudo apt-get install packagename" normally.  xorg-dev is a development meta-package (it depends on a bunch of other *-dev packages) so you wouldn't build it.  You should try to install packages from the repositories before you try to build them from source.  You'll run into fewer problems that way.  So when the ./configure step spits out errors, use aptitude or synaptic to search for packages that include the library name in the error message.  You'll want to install the ones that end in "-dev" since debian packages are split between the normal runtime libraries and the development versions used when compiling.

---

