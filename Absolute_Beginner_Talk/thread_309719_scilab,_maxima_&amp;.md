---
title: "scilab, maxima &amp;"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by padeco on 2006-11-30
hi there,

two points to ask:

1-
 here we go again, having some dificulties installing scilab. i did the synaptic, apt-get and aptitude install, however, all three install an earlier version with hindi scripts! great stuff.

downloaded the source from the scilab webpage, and followed the instructions on the README_Unix file:
-->
  B - IF YOU HAVE A SOURCE VERSION
  --------------------------------
  
    This distribution has been tested on the following machines:
    SUN Sparcstation (Solaris 5.8), HPUX workstation c8000 (HP.UX 11.11) and PC linux
    (Mandriva 9.2,2005,2006, Fedora Core IV, Red Hat 9.0, Suse 10.0). But it should work on
    other UNIXes.
    
    You need X Window (X11R4, X11R5 or X11R6), C compiler and Fortran compiler.
    
    1 - Configure your system by issuing the following command in the Scilab 
        directory:
        ./configure

GOT THIS!!!!!
~/Programs/scilab-4.0$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
Humm... this is a binary version
  you'd better read the README file first.

any help?


2- the second issue. synaptic, apt-get and aptitude all have the earlier versions of maxima and wxmaxima which do not work well on ubuntu 6.0.6. how do i go about to access something that will install the two programs with all the dependencies file?

manu thanks,
padeco

---

### Post by padeco on 2006-11-30
with regards to the maxima and wxmaxima, the issue has been solved having found the following link:

[http://www.ubuntuforums.org/showthread.php?t=305788&highlight=wxmaxima](http://www.ubuntuforums.org/showthread.php?t=305788&highlight=wxmaxima)
> Hello,

We finally have a fix for the awful maxima frontend breakage in 6.06 (dapper). We need people to test the fix before it is uploaded to dapper-updates. What you need to do is add:
Code:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-proposed main universe

to your apt sources (/etc/apt/sources.list) and then update. The 2 packages that are specifically needed are gcl and maxima. If you test this out (making sure a maxima GUI like xmaxima or wxmaxima work) please add a comment to [https://launchpad.net/distros/ubuntu...ima/+bug/43150](https://launchpad.net/distros/ubuntu...ima/+bug/43150)

Thanks.

-LaserJock

---

### Post by odelay on 2007-02-23
For 1.

You most likely downloaded the binary version, not the source version.  You're missing the preceding section in the README that says:

> A - IF YOU HAVE A COMPILED VERSION
  ----------------------------------

    Simply do, in Scilab directory:
      make
Depending on what directory you unpacked the scilab folder in, you might need to change it to "sudo make".

---

