---
title: "anyone able to compile any X programs on ubuntu"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-06
since dloading ubuntu 4 days ago, i have had a very slim rate of "hits" in things i've tried to do;
i aint goin' give in...but god, i'm having a hard time of it!
i'm currently trying to do what seems like a pretty humble task of installing a chess program called xboard, based gnuchess...

i'm following the guide provided by the author, but have hit hitch after hitch...
the latest concerns the following topic subheading in author's notes:

"Configuring or building XBoard fails due to missing header files, missing libraries, or undefined symbols."

He suggests that I might: 

"have the X server and client programs installed on your machine, but not the X header files and link-time libraries. If so, you can run existing X programs, but you cannot compile a new X program from source code. In this case the XBoard configure script will fail and will tell you to look at this question in the FAQ. Many GNU/Linux distributions put the headers and libraries in a separate package, which you might not have installed. If you are using RedHat, install the XFree86-devel package. If you are using some other kind of Unix, ask your system administrator where to find the X header files and link-time libraries. "

cd someone help me out with this?
i really need to start getting a leeeetle bit of pleasure for all this patient sweating and getting nowhere..
frustrated but resigned to total abstinence from windoze,
rufus

---

### Post by freebird54 on 2007-05-06
I think **build-essential** is the package you're missing.

---

### Post by Nythain on 2007-05-06
this might help ya out a bit
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

```

---

### Post by rufi_dukes on 2007-05-07
sigh...
i wonder how long before i can do that...
thanks kindly,
rufus

---

### Post by rufi_dukes on 2007-05-07
ran the code u gave me and saw heaps of script scroll past,
then went back to author's code for making xboard,
only to get same result, last lines of which i quote:

xboard requires the X Window System header files and libraries!
They were not found on your system. See FAQ topic C.2.
configure failed
michael@michael-desktop:~/xboard-4.2.7$

arrrrgggghhhhh,
rufus

---

