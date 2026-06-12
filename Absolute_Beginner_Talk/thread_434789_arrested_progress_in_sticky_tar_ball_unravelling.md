---
title: "arrested progress in sticky tar ball unravelling"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-06
i found a chess prog that i'd like to install and use; it's called xboard;
i also got the code for installing it, tried entering the code at prompt and got the result below...
i'm loathe to abandon attempt at this point;
cd someone stick a friendly nose in here and suggest a way out?
first, the code that was given me,
then then the last line of that code which i entered before getting the final output containg the error:

gzip -cd xboard-*.tar.gz | tar -xvf -
    cd xboard-*/
    ./configure
    make
    su
    make install


michael@michael-desktop:~/xboard-4.2.7$ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
michael@michael-desktop:~/xboard-4.2.7$
michael@michael-desktop:~/xboard-4.2.7$

thx kindly for any help,
rufus

---

### Post by Happy_Man on 2007-05-06
You need to install build-essential first:
```
sudo apt-get install build-essential
```

---

### Post by rufi_dukes on 2007-05-06
i did what u suggested and that seemed to go alright, so then i re-ran the script i quoted in my original mail, only to be told that, when ...

checking for X... no
xboard requires the X Window System header files and libraries!
They were not found on your system. See FAQ topic C.2.
configure failed

so, i consulted faq topic c2, to be told:


"Perhaps you have the X server and client programs installed on your machine, but not the X header files and link-time libraries. If so, you can run existing X programs, but you cannot compile a new X program from source code. In this case the XBoard configure script will fail and will tell you to look at this question in the FAQ. Many GNU/Linux distributions put the headers and libraries in a separate package, which you might not have installed. If you are using RedHat, install the XFree86-devel package. If you are using some other kind of Unix, ask your system administrator where to find the X header files and link-time libraries. If this is not your problem, read on. 

The configure script for XBoard looks for X libraries and header files in some common places. Sometimes it fails: If yours are installed in an odd place, it may not find them at all. If you have more than one version of X installed on your system, it may find the "wrong" one, or occasionally it may find libraries from one version and incompatible header files from another. You can work around these problems by telling the configure script where the files are. For example: 

    configure --x-includes=/odd/place/include \
              --x-libraries=/odd/place/lib

The directory named in the argument to --x-includes must have a subdirectory "X11" that contains the actual .h files. That is, if your X.h file has full pathname /odd/place/X11R6/include/X11/X.h, then you must give the argument --x-includes=/odd/place/X11R6/include. 

Some linkers have bugs that cause bogus error messages when you try to link X programs. The configure script includes a workaround for a bug of this kind that exists in some SunOS 4.x.x installations. See the FAQ on comp.windows.x for more information about problems of this kind. 

If all else fails, check whether anyone else at your site has been able to compile any X programs on your system. Your X installation might be buggy. If so, the system administrator at your site might know how to fix or work around the problem. 

Also see topic [C.1].

at the risk of pushing the bounds of patience, 
i have pasted topic c.1:

C.1] I can't build XBoard because the X11/Xaw/... include files are not found.
These are the header files for the Athena Widgets library, which XBoard uses heavily. Some versions of Unix don't supply these files, but they are part of the standard X distribution, freely available from MIT. 

For general information on getting missing X sources, see the FAQ on comp.windows.x. Note that you may be missing only the header files, or you may be missing the libraries themselves too. 

HP-UX users are missing only the header files. You can get them by anonymous FTP as follows. (But first check with your system administrator to see if someone else at your site has already done this.) Get the archive file /hpux9/X11R5/Core/Xaw-5.00.tar.gz (Xaw header files) via anonymous FTP from the site hpux.csc.liv.ac.uk (138.253.42.172), or one of the other official sites---Germany: hpux.ask.uni-karlsruhe.de (129.13.200.57), US: hpux.cae.wisc.edu (144.92.4.15), France: hpux.cict.fr (192.70.79.53) or Netherlands: hpux.ced.tudelft.nl (130.161.140.100). Unpack the archive using gzip and follow the instructions in its README and/or HPUX.Install files. Thanks to Richard Lloyd for this information. 

If you have the Xaw header files installed in a different place than the other X11 headers, you may need to configure XBoard with an extra flag to help it find them. For example, if yours are in /foo/bar/X11/Xaw, try this: 

    rm config.cache
    (setenv CFLAGS -I/foo/bar ; configure)

Also see topic [C.2].

what do u make of that?
it is all completely mysterious to me, a total fledgling with little stumpy penguin wings...
rufus

---

### Post by Happy_Man on 2007-05-07
That's quite interesting.... it seems that Ubuntu skimped and decided not to install essential libraries. I would open up Synaptic, search for X, and just install whatever seems essential to the X window system.

---

### Post by rufi_dukes on 2007-05-07
thx happy,
i'll give that a go...
rufus

---

