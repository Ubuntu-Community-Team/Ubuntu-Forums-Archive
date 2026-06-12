---
title: "unixtree libncurses.so.4: cannot open shared ob ject file:"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by rmpowell01 on 2008-02-26
Downloaded the Xtree Clone - Unixtree file manager tar.gz. Verison 2.3.0. from Twocows. Followed install guide and all went fine, after some learning time. When I try to run XT I receive this message:

xt: error while loading shared libraries: libncurses.so.4: cannot open shared object file: No such file or directory

I could not find Libncurses.so.4 with Synapic Package manager so I installed Livsureses.so.5. But this did not help. 

I am out of ideas.

Opinion: I know that I am suppose to like command line controls if I use Linux, but I don't. That is why I want Unixtree. If Gnome or KDE GUI's could provide a tar.gz installer like what is available for ,deb. I think a lot more windows boxes would be switched to Linux. For those of you that think I am nuts I will make two points. 1. The average computer user has no interest in learning or using a command line computer. 2. MS is successful because the user does not need any special knowledge to install and use any program package they desire.

---

### Post by jw5801 on 2008-02-27
The whole point of .deb and similar packages is to negate the need for installing from source. A ".tar.gz" package is simply the source code of the application, compressed. It needs to be compiled and then installed, via ./configure; make; make install. Depending on your system and setup and where everything else is installed to, autoconf (the backend for "make") needs to be called differently. In modern distributions there is no need to install from source, hence the user does not require any special knowledge to install a package. It just needs to be in the right format, a .deb for a debian based distribution.

Anyway, on to the problem. This application is looking for an older version of the libncurses shared library than is included in Gutsy. The best option would be to find a newer version of the software you're after. Looking at sourceforge shows that a release hasn't been made since 2005, so it might be a dead project, and, to give you a Windows analogy, running it on Gutsy is probably going to be like trying to run an Win95 program on XP, it might work, but it might be buggy and it might take some effort to get it running.

My first approach would be to try to create the old library by symlinking it to the newer one, first check you have the libncurses library. The following command should give you a similar output to below:
```
jw5801@jw5801:~$ ls -l /lib | grep libncurses
lrwxrwxrwx  1 root root      17 2008-02-14 10:42 libncurses.so.5 -> libncurses.so.5.6
-rw-r--r--  1 root root  375920 2007-10-08 20:29 libncurses.so.5.6
lrwxrwxrwx  1 root root      18 2008-02-14 10:42 libncursesw.so.5 -> libncursesw.so.5.6
-rw-r--r--  1 root root  425424 2007-10-08 20:29 libncursesw.so.5.6
```

If it doesn't look something vaguely like that (you should at least have a libncurses.so.5 file) then you don't have libncurses at all, so install the package (sudo apt-get install libncurses). If you have then try creating the symlink to the newer library:
```
sudo ln -vs /lib/libncurses.so.{5,4}
```

Then try running the program again and see if it works.

---

### Post by rmpowell01 on 2008-02-28
ran the commands you suggested, here is the results:
ls -l /lib | grep libncurses
lrwxrwxrwx  1 root root      17 2008-02-23 22:59 libncurses.so.5 -> libncurses.so.5.5
-rw-r--r--  1 root root  262860 2006-01-13 12:55 libncurses.so.5.5
lrwxrwxrwx  1 root root      18 2008-02-23 23:00 libncursesw.so.5 -> libncursesw.so.5.5
-rw-r--r--  1 root root  299916 2006-01-13 12:55 libncursesw.so.5.5

 sudo ln -vs /lib/libncurses.so. {5,4}
Password:
ln: target `4' is not a directory


As you can see I still have problem

---

### Post by jw5801 on 2008-02-28
There shouldn't be a space between the libncurses.so. and the {5,4} :p

It's a shorter way of writing:
```
sudo ln -sv /lib/libncurses.so.5 /lib/libncurses.so.4
```

The {5,4} means that there should be two inputs to stdin, one of 5 and one of 4. It's a useful shorthand bash trick.

---

