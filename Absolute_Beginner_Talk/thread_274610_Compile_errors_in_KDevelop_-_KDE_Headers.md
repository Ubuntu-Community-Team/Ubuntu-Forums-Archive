---
title: "Compile errors in KDevelop - KDE Headers"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Jamhos on 2006-10-10
Hey :)

I'm running Kubuntu (the latest one, I suppose :P), and I tried to make my first "Hello World" program in KDevelop. But after I did *Run --> Compile*, I got an error saying:

[I]checking for KDE... 
configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix![/I]

I looked around a bit on the forums and other sites, and gathered that I needed the package *kdebase-dev*, but when I tried to install it using Adept, it said it would break stuff (it actually seems, reading the description, that this should be installed already, but my system is running fine without it, so yeah!).

Anyway, to discover what exactly what was causing the thing to break, I clicked on "Details", and it gave me a list of packages it would install when installing kdebase-dev (dependencies, I guess). I found that it was one of the dependencies that was actually causing the break - *kdelibs4-dev*.

So again, I found which dependency was causing the problem, and it turned out to be *libarts1-dev*, which in turn was having it's problem caused by *libartsc0-dev*. Turns out that libartsc0-dev is the one screwing everything up, but I have no idea why. I am thinking this would solve the problem, but if it doesn't, at least I might have learnt something! (That's the thing I love most about Ubuntu!).

Any help would be greatly appreciated! Thanks :)

---

### Post by elettronicha on 2006-10-10
- Are you sure of what kubuntu version you're running?

- Did you install the package 'build-essential'?

- Did you enable the repository needed? (see the official kubuntu guide)

Anyway, I don't think the KDE headers are necessary to compile a simple 'hello world' program. 

;)

---

### Post by Jamhos on 2006-10-10
- It's Kubuntu 6.06 - sorry, I should've known that :P
- Yeah, that's the first thing I did :)
- Um... not sure which repository you mean, but I have enabled several new ones to try to combat this issue.

Yeah, I actually compiled some drivers for a wireless network card last night without any problems (once I installed some other stuff *sigh*), so I really don't know what the problem is. Maybe I'll try Python - apparently it's pretty good. Thanks for your help anyway!

---

### Post by Jamhos on 2006-10-11
Well, I updated my sources.list from some website, and I was able to install kdebase-dev at last, and my program will compile. But now I have yet another problem!

When I click *Build --> Install*, I get this output:

> cd '/home/james/Programs/sigcreate/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k install
Making install in doc
Entering directory /home/james/Programs/sigcreate/debug/doc
Making install in .
Entering directory /home/james/Programs/sigcreate/debug/doc
Entering directory /home/james/Programs/sigcreate/debug/doc
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
Leaving directory /home/james/Programs/sigcreate/debug/doc
Leaving directory /home/james/Programs/sigcreate/debug/doc
Making install in en
Entering directory /home/james/Programs/sigcreate/debug/doc/en
Entering directory /home/james/Programs/sigcreate/debug/doc/en
make[3]: Nothing to be done for `install-exec-am'.
creating /usr/local/kde/share/doc/HTML/en/sigcreate
installing /usr/local/kde/share/doc/HTML/en/sigcreate/index.docbook
installing denied
make[3]: *** [install-nls] Error 1
make[3]: Target `install-data-am' not remade because of errors.
Leaving directory /home/james/Programs/sigcreate/debug/doc/en
Leaving directory /home/james/Programs/sigcreate/debug/doc/en
make[2]: *** [install-am] Error 2
make[2]: Target `install' not remade because of errors.
make[1]: *** [install-recursive] Error 1
make[1]: Target `install' not remade because of errors.
Leaving directory /home/james/Programs/sigcreate/debug/doc
Making install in po
Entering directory /home/james/Programs/sigcreate/debug/po
Entering directory /home/james/Programs/sigcreate/debug/po
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
Leaving directory /home/james/Programs/sigcreate/debug/po
Leaving directory /home/james/Programs/sigcreate/debug/po
Making install in src
Entering directory /home/james/Programs/sigcreate/debug/src
Entering directory /home/james/Programs/sigcreate/debug/src
test -z "/usr/local/kde/bin" || mkdir -p -- "/usr/local/kde/bin"
installing '/usr/local/kde/bin/sigcreate'
installing denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Target `install-exec-am' not remade because of errors.
creating /usr/local/kde/share/icons/hicolor/16x16/apps
installing /usr/local/kde/share/icons/hicolor/16x16/apps/sigcreate.png
installing denied
test -z "/usr/local/kde/share/applnk/Utilities" || mkdir -p -- "/usr/local/kde/share/applnk/Utilities"
make[2]: *** [install-kde-icons] Error 1
installing '/usr/local/kde/share/applnk/Utilities/sigcreate.desktop'
installing denied
make[2]: *** [install-shelldesktopDATA] Error 1
test -z "/usr/local/kde/share/apps/sigcreate" || mkdir -p -- "/usr/local/kde/share/apps/sigcreate"
installing '/usr/local/kde/share/apps/sigcreate/sigcreateui.rc'
installing denied
make[2]: *** [install-shellrcDATA] Error 1
make[2]: Target `install-data-am' not remade because of errors.
Leaving directory /home/james/Programs/sigcreate/debug/src
Leaving directory /home/james/Programs/sigcreate/debug/src
make[1]: *** [install-am] Error 2
make[1]: Target `install' not remade because of errors.
Entering directory /home/james/Programs/sigcreate/debug
Entering directory /home/james/Programs/sigcreate/debug
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
Leaving directory /home/james/Programs/sigcreate/debug
Leaving directory /home/james/Programs/sigcreate/debug
make: *** [install-recursive] Error 1
make: Target `install' not remade because of errors.
*** Exited with status: 2 ***

I really have no idea where to go now!

---

### Post by Jamhos on 2006-10-13
*bump*

Please help, I really love programming, but am yet to figure it out in Linux!

---

