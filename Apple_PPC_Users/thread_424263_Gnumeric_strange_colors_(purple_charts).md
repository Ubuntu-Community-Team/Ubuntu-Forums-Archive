---
title: "Gnumeric strange colors (purple charts)"
date: 2007-04-26
forum: Apple PPC Users
---

### Post by mambro on 2007-04-26
Have you ever experienced this?
[https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/109204](https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/109204)

why in ubuntu there's 1.7.8 version that is a development version? :(

---

### Post by ssam on 2007-04-26
yes

i have spoken to the devs, and they seem to have found the problem. something to do with macros for converting between colourspaces, which are not endian safe. if this is the problem then they just need to do some tests, to figure out what the macros should do on powerpc.

in the mean time i have downgraded to edgy packages 1.7.0.

you will need to uninstall gnumeric and goffice (the actual bug is in the goffice code).

then install the following packages

[http://librarian.launchpad.net/4446063/gnumeric_1.7.0-1ubuntu4_powerpc.deb](http://librarian.launchpad.net/4446063/gnumeric_1.7.0-1ubuntu4_powerpc.deb)
[http://librarian.launchpad.net/4446064/gnumeric-plugins-extra_1.7.0-1ubuntu4_powerpc.deb](http://librarian.launchpad.net/4446064/gnumeric-plugins-extra_1.7.0-1ubuntu4_powerpc.deb)
[http://librarian.launchpad.net/4446054/gnumeric-common_1.7.0-1ubuntu4_all.deb](http://librarian.launchpad.net/4446054/gnumeric-common_1.7.0-1ubuntu4_all.deb)

[http://librarian.launchpad.net/3296635/libgoffice-0-common_0.3.0-1ubuntu1_all.deb](http://librarian.launchpad.net/3296635/libgoffice-0-common_0.3.0-1ubuntu1_all.deb)
[http://librarian.launchpad.net/3373586/libgoffice-0-3_0.3.0-1ubuntu1_powerpc.deb](http://librarian.launchpad.net/3373586/libgoffice-0-3_0.3.0-1ubuntu1_powerpc.deb)

you can install a package with
```
dpkg -i packagename.deb
```

---

### Post by mambro on 2007-04-27
Good! I hope they will resolve the problem soon :) 
For now i will not downgrade because i don't need gnumeric for the next 2 weeks.. if they don't fix the problem in 2 weeks i will downgrade :wink: 
Thank you for the answer

---

### Post by ssam on 2007-04-27
ok the bug is fixed upstream.

the bug was in goffice.

if you install the ubuntu feisty packages, then download

[http://tygier.co.uk/pub/libgoffice-0-3_0.3.7-0ubuntu1_powerpc.deb](http://tygier.co.uk/pub/libgoffice-0-3_0.3.7-0ubuntu1_powerpc.deb)

and install with the command

```

sudo dpkg -i libgoffice-0-3_0.3.7-0ubuntu1_powerpc.deb

```

in the directory that you downloaded it to.

let me know if there are any problems

i'll see if i can get this accepted officially into ubuntu.
----
if this works for you could you please comment on [https://bugs.launchpad.net/ubuntu/+source/goffice/+bug/109204](https://bugs.launchpad.net/ubuntu/+source/goffice/+bug/109204)

---

### Post by mambro on 2007-04-27
Good job! It's perfect!! thank you :wink:

---

### Post by mambro on 2007-04-29
When it will be disponible through  software update?

---

### Post by ssam on 2007-05-25
my exams are finished so i did some work on this bug.

I proposed a [stable release update]("https://wiki.ubuntu.com/StableReleaseUpdates"), but it apparently does not meet the criteria. (i know some people don't like this but its part of the way ubuntu works.)

hopefully version 0.4 of goffice will get into gutsy soon, and then we can ask for a backport.

until then i have made a fixed version with an updated version number (i should have done this to start with). this will stop apt trying to 'up date' you back to the official version.

[http://tygier.co.uk/pub/libgoffice-0-common_0.3.7-0ubuntu1.1_all.deb](http://tygier.co.uk/pub/libgoffice-0-common_0.3.7-0ubuntu1.1_all.deb)
[http://tygier.co.uk/pub/libgoffice-0-3_0.3.7-0ubuntu1.1_powerpc.deb](http://tygier.co.uk/pub/libgoffice-0-3_0.3.7-0ubuntu1.1_powerpc.deb)

they can both be installed by double clicking. install the common one first.

if you want to build your own packages try this
```

sudo apt-get build-dep goffice
sudo apt-get install devscripts fakeroot
mkdir goffice
cd goffice
apt-get source goffice
cd goffice-0.3.7
wget http://librarian.launchpad.net/7781051/fix_purple_charts.patch
patch -p1 < fix_purple_charts.patch
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i libgoffice-0-common_0.3.7-0ubuntu1.1_all.deb 
sudo dpkg -i libgoffice-0-3_0.3.7-0ubuntu1.1_powerpc.deb 

```
(i may have missed something out, so let me know if this does not work)

---

