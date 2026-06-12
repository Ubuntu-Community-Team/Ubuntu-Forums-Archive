---
title: "trouble compiling freeciv2  v1.14.2"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by cjh on 2006-09-01
hi, can anyone please help me figure this out?

i686 pc, running ubuntu 6.06LTS

i am trying to install freeciv2 version 1.14.2. i have solved a few problems so far yet i cannot get past this problem whilst compiling the code:


[I]checking extra paths for Xpm... library no, include no
checking for XOpenDisplay in X library -lX11... no
configure: error: specified client 'xaw' not configurable -- need X11 libraries and development headers; perhaps try/adjust --x-libraries[/I]


i have searched all over the forums, the repositories and the net and cannot find any info about X11. can someone please help me figure this out?

---

### Post by DonS on 2006-09-01
Hi,

There is a version of Freeciv in the repos.  resuming you want to compile it yourself (its a later version...), the easy way to do it is to run:
> sudo apt-get build-dep freeciv-client-gtk
Which should install all the necessary libraries to build freeciv.

Alternatively, search through the repositories for 'X11'.  The '-dev' versions there will contain the required headers.  There is also (I think) a 'meta-package', a package that will pull in all the X11 header files, allowing you to compile programs.  Unfortunately, I'm away from by Ubuntu machine right now, so can't check.

You're best bet is to do the 'build-dep' way described above though.  For more info about what X11 is about, check out [wikipedia]("http://en.wikipedia.org/wiki/X_Window_System"), though the discussion is fairly technical.  (Ubuntu uses Xorg 7.0 if you're reading the article)

---

### Post by cjh on 2006-09-09
hi DonS,

thanks for replying. i have had a bad week so sorry for not responding sooner.
it turns out i have already installed the freeciv-client-gtk package as well as every x11 package i could find. i managed to get the program to compile using some other commands. though now when trying the "make install" command this is the response i get:

[I]cjh@cjh-desktop:~/Games/fcb2/fcb22$ make install
Making install in data
make[1]: Entering directory `/home/cjh/Games/fcb2/fcb22/data'
Making install in amplio
make[2]: Entering directory `/home/cjh/Games/fcb2/fcb22/data/amplio'
make[3]: Entering directory `/home/cjh/Games/fcb2/fcb22/data/amplio'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/freeciv/amplio" || mkdir -p -- "/usr/local/share/freeciv/amplio"
mkdir: cannot create directory `/usr/local/share/freeciv': Permission denied
make[3]: *** [install-pkgdataDATA] Error 1
make[3]: Leaving directory `/home/cjh/Games/fcb2/fcb22/data/amplio'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/cjh/Games/fcb2/fcb22/data/amplio'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/cjh/Games/fcb2/fcb22/data'
make: *** [install-recursive] Error 1[/I]

I do not understand any of this and wonder is the permission denied anything to do with root? because i am admin logged in. 
sorry, but being newbie doesnt help much i suppose. i really appreciate your help.

---

