---
title: "Makehuman 64bit installation - success, sharing my experience"
date: 2007-11-07
forum: Art &amp; Design
---

### Post by sigdrifa on 2007-11-07
Hi all!
I ran into some problems with the installation of Makehuman on a 64bit Gutsy installation. I solved it, however, and I want to share my experience here for others who run into the same problem.

At first I downloaded the .deb files. They are i386, so I installed them via --force-architecture, and that worked all right.
(Note: Makehuman depends on freeglut3, which can be installed from the Ubuntu main repository)
But when I tried to run makehuman, I got an error about missing libmhgui. I knew I had installed all five packages I downloaded, so I suspected an architecture compatibility problem. I removed the debs, and downloaded the source.
Compiling required to install freeglut3-dev, of course, but otherwise went without errors. The correct order to make and install the three programs is
1. animorph
2. mhgui
3. makehuman
However, after the last make install I tried to run makehuman, and it returned "/usr/bin/makehuman: command not found."
?
So, I decided to start all over, this time with the prefix option in configure. I went back to the directory containing the source and typed 'make uninstall'. I forgot sudo, which of course resulted in a "permission denied" error. But that little mistake actually helped solving the problem, because in that error I saw that make was trying to uninstall from /usr/*local*/bin.
When I tried to run /usr/local/bin/makehuman I didn't get a "command not found" error, but rather that error about missing libmhgui, the one I also got with the debs. So I checked /usr/local/lib, and there they where: libanimorph and libmhgui.
I created symlinks in /usr/bin and /usr/lib, and voilà, everything works.
Now I just have to learn how the program works.

Only one hint to the inexperienced user: Makehuman requires an external renderer. I had installed the Yafray engine before, but that didn't work. I installed aqsis, and that did.

Happy modelling everyone :)

---

### Post by Unterseeboot_234 on 2007-11-12
When I was running Dapper, I made 64-bit debs of makeHuman. After double-click installation of the debs, a command-line

```
makeHuman
```

brings up the application running. My debs install in the Home folder is my only complaint. I tried to rebuild in Gutsy, but with no luck. Thank goodness I have the debs sitting in an online file storage. Anyone is welcome to the .debs. Follow along from another Forum discussion to get to the link(s).

**[Forum makeHuman]("http://ubuntuforums.org/showthread.php?t=333615")**


I only mention this as the debs that I posted are 64-bit for the AMD.

---

