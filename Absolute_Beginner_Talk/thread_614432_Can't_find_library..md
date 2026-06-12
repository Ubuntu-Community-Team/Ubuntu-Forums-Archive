---
title: "Can't find library."
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-15
I'm trying to get a game running, but it doesnt work when i doubleclick the crx.sdl file it doesn't work.  So i tried running it from the terminal and it gives me this error:

jordan@Jorcomp:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

i'm assuming this means i need the "libXxf86dga.so.1" library?  When i type:
sudo apt-get install libXxf86.dga.so.1 it just gives me:

jordan@Jorcomp:~$ sudo apt-get install libXxf86.dga.so.1
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libXxf86.dga.so.1

what's the problem here?

---

### Post by odiseo77 on 2007-11-15
Try this:

```
sudo apt-get install libxxf86dga1
```

If there aren't other unmet dependencies, it should be fine.

---

### Post by jordank on 2007-11-15
jordan@Jorcomp:~$ sudo apt-get install libxxf86dga1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxxf86dga1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jordan@Jorcomp:~$ 

what's the prob?

---

### Post by ramjet_1953 on 2007-11-15
The reason you couldn't download it is because you typed the syntax incorrectly.

Try this:

> [COLOR="Red"]sudo apt-get install libxxf86dga1[/COLOR]

You may also need the development files, try it first without them, though.

> [COLOR="Red"]sudo apt get install libxxf86dga-dev[/COLOR]

Regards,
Roger 8)

---

### Post by jordank on 2007-11-15
what was wrong with my syntax in your first quote?

---

### Post by odiseo77 on 2007-11-15
The package name is not libXxf86.dga.so.1 but ***libxxf86dga1***, that's why you got that error when you try to install it that way, the name you typed is the name of one oçf the development components/files of the library :) (in fact, I just checked and you need the 'libxxf86dga-dev' package, as ramjet_1953 says). :-)

---

### Post by zabien1970 on 2007-11-15
Just noticed in the thread starter the  first x in libXx is capitalized, could this make a difference?

Edit: nevermind, just seen the post above

---

### Post by jordank on 2007-11-16
jordan@Jorcomp:~/Desktop/alienarena2007$ sudo apt-get install libxxf86dga1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxxf86dga1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jordan@Jorcomp:~/Desktop/alienarena2007$ sudo apt-get install libxxf86dga-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxxf86dga-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jordan@Jorcomp:~/Desktop/alienarena2007$ ./crx.sdl
./crx.sdl: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory


like everything seems to be up to date and there. i dont understand why i can run this. it still seems like i'm missing libraries.

---

### Post by jordank on 2007-11-16
and yeah, i checked if the X made a difference, it doesnt.

---

### Post by jordanmthomas on 2007-11-16
I usually just make a symbolic link to whatever version I already have (probably a bad thing but it usually works).
```
ls /usr/lib | grep libXxf8
```
what does this show?

---

### Post by jordank on 2007-11-16
jordan@Jorcomp:~$ ls /usr/lib | grep libXxf8
libXxf86dga.a
libXxf86dga.so
libXxf86dga.so.1
libXxf86dga.so.1.0.0
libXxf86misc.so.1
libXxf86misc.so.1.1.0
libXxf86vm.so.1
libXxf86vm.so.1.0.0

---

### Post by jordanmthomas on 2007-11-16
That is definitely strange:  libXxf86dga.so.1 is already there.
This is one of those, "sorry my idea won't be of any use to you" type of deals.  Sorry.

---

### Post by jordank on 2007-11-16
haha, what should i do from here?

---

### Post by Hooya on 2008-07-01
Did you ever find the answer to this problem?  I'm having the exact same issue.  Hardy 64-bit version (probably the problem is I'm running 64 bit, right?)

---

