---
title: "Astrophysicist needs GNUPLOT"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by dwdarkstar on 2008-02-01
I have been asked by a colleague to generate a number of plots using a new set of stellar pulsation models which will be placed into a research paper for submission to various scientific journals.  I have been learning to use Linux by trial and error over the last two years.  In attempting to install GNUPLOT for terminal use, I have error'ed myself beyond comprehension.  I successfully installed GNUPLOT last month however the terminal output was poor, I guess I neglected to install the X11 software required.  In an attempt to correct this, I tried to reinstall gnuplot using instructions from the web located here:
[http://www.miscdebris.net/blog/2008/01/23/install-gnuplot-on-ubuntu-gutsy-gibbon/](http://www.miscdebris.net/blog/2008/01/23/install-gnuplot-on-ubuntu-gutsy-gibbon/)
While compiling gnuplot I tried to remedy the descriptions under the fourth bullet related to terminal support.  This spiraled into an installation frenzy so vicious I have lost sight of my original objective, to be able to run gnuplot from the command prompt.  Worse, gnuplot no longer functions in my terminal, and I am at a loss as to what to do now.  My instinct is to undo everything and start fresh, but I don't know how to do this either.  I appeal to my computer savvy brethren in arms.  man gnuplot might have helped in the beginning but is useless to me now.  My terminal response is:

farstar@farstar-laptop:~$ gnuplot
gnuplot: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libpdf.so.6)

I should also mention that I have attempted to install many packages since learning the basic terminal commands, most of these have been failures.   I actually have a file on my desktop called Failures.  It took me 6 months to get eboard and xboard working so I could play GNUchess.  In this case I don't have 6 months.   Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2008-02-01
gnuplot is in the repos, in universe

Enable your reops, then

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

```
sudo apt-get update && sudo apt-get install gnuplot
```

[http://packages.ubuntu.com/hardy/math/gnuplot](http://packages.ubuntu.com/hardy/math/gnuplot)

post any errors

---

### Post by eapache on 2008-02-01
Assuming that you don't have any data saved in gnuplot that you need, try```
sudo apt-get purge gnuplot
sudo apt-get install gnuplot
```

---

### Post by bodhi.zazen on 2008-02-01
This information may also help you :

> This package is for transition and to install a full-featured gnuplot supporting the X11-output. **If you want to skip the X-windows-dependency (e.g. if you're running a small server) just install "gnuplot-nox" and skip this meta-package.**

---

### Post by dwdarkstar on 2008-02-01
I enabled the repositories.  Then tried eapache's suggestion to purge gnuplot.  I have previously tried to negotiate the package at the ubuntu link you provided with out success.  Terminal results below:


farstar@farstar-laptop:~$ sudo apt-get purge gnuplot
Password:
E: Invalid operation purge
farstar@farstar-laptop:~$ sudo apt-get update && sudo apt-get install gnuplot
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 2B in 0s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
gnuplot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
farstar@farstar-laptop:~$ gnuplot
gnuplot: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libpdf.so.6)

---

### Post by bodhi.zazen on 2008-02-01
OK, sorry you are having problems. I just installed gnuplot without any problem, so I am guessing you have a conflict with some package you have installed from source.

You can try this, purge. The command is off a little in the previous post, sorry I did not catch that earlier.

```
sudo apt-get remove --purge gnuplot
```

Note: there are two - - in front of purge

Now lets try re-installing :

```
sudo apt-get install gnuplot
```

If that fails, we will need to purge it again, and then remove any source package you tried to install.

you can do this with:

1. cd into the extracted archive (where you ran /.configure , make , sudo make install).

Try : ```
sudo make uninstall
```

2. If that fails, you will need to remove the package manually. Do this with :

```
sudo updatedb
locate <package_name>
```
now sudo rm those packages.

:(

Once you are done with that, and everything has been removed / purged, manually if necessary, then :

```
sudo apt-get install gnuplot
```

============

The only other option is to start with a fresh install (up to you which may take less time).

If you go with a fresh install, 

the gnuplot from the repository looks to be a "meta package" and includes X support. gnuplot-nox = no X support.

============

And one last FYI, in the future, take a look at either compiling in a chroot and / or checkinstall.

Checkinstall builds a .deb from the source package, making both installation and removal easier. It does not always work mind you.

chroot :
[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)


checkinstall :

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
	[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)


================

HTH, let me know if you get stuck during this process.

---

### Post by dwdarkstar on 2008-02-02
IT WORKS!  I just plotted the most beautiful straight line I've ever seen.  Wow, I followed your instructions, the --purge failed, the uninstall failed, rm that libpdf.so.6 failed.  I started to get nervous, but with your help and help.ubuntu.com I was able to search and destroy anything related to gnuplot.  I then updatedb, apt-get install gnuplot, and it failed.  Turns out I got a bit trigger happy and rm some dir, including gnuplot.  mkdir gnuplot, reload apt-get....SUCCESS!

Thank you very much bodhi.zazen, not only did you help me correct my issue, I learned quite a bit in the process.  Give a physicist some code and he computes for a day, teach a physicist to code and he computes for a lifetime.

---

