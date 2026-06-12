---
title: "Installing / Compiling tar.gz files (Missing build-essential)"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by 9400 on 2007-08-20
Before I ask my question, I want to get one thing straight - I am a big time newb, technical-wise and Linux-wise.

Anyway, I downloaded a program with the tar.gz extension.  I quickly found out that this was an installer for Linux.  I figured out how to extract it, but it didn't run,  But after some quick Googling I found out that it was source code and that I needed to compile it.  I started to follow a tutorial, and immediately ran into a problem - I couldn't find the build-essential package.  I found a few more, and they all needed the build-essential package.  Now I was getting worried :D.  I found one that didn't need it, but it seemed awful complicated :D.  So now I turn to the Ubuntu Community, which has helped me before.  Where the heck can I find the build-essential package?

I have tried searching Synaptic for build-essential - nothing.  Same with Add/Remove applications.  In the terminal, I have tried both sudo apt-get install build-essential and sudo synaptic install build-essential, both with and without install.  All 4 times it said it couldn't find the package.  (Yes, I'm connected to the internet :D)  I know of no other way to get it.  Can someone possibly help?

Thanks in advance.

PS - This forum has ownage smilies :guitar::lolflag:

---

### Post by Paul133 on 2007-08-20
sudo apt-get install build-essential should work, although you may need to enable some repositories. Enable Universe and Multiverse. I think it's in one of those. Go to Synaptic and click on repositories. Make sure they're all checked. Then search for build-essential again. Did that help?

edit: Just checked and it seems build-essential is not in universe or multiverse (though it's still good to have them enabled). It should be in Synaptic under the section 'Development', right after bsh and before byacc.

---

### Post by taurus on 2007-08-20
Which release are you running?  Try running

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by logos34 on 2007-08-20
Do you have the Main repository enabled in Synaptic Software sources?

$ apt-cache show build-essential
Package: build-essential
Priority: optional
Section: devel
Installed-Size: 48
Maintainer: Matthias Klose <doko@debian.org>
Architecture: i386
Version: 11.3
Depends: libc6-dev | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)
Filename: pool/[COLOR="Red"]main[/COLOR]/b/build-essential/build-essential_11.3_i386.deb
Size: 6974
MD5sum: 9555bbff826c8f059d00a824d6285275
SHA1: f6ac750100f9e72011a3f29662da61125d7babd2
SHA256: 1a0cc1567004994fb0bc80bc06c3b7446b1972057d9f9ea202f1817147586b52
Description: informational list of build-essential packages
 If you do not plan to build Debian packages, you don't need this
 package.  Moreover this package is not required for building Debian
 packages.
 .
 This package contains an informational list of packages which are
 considered essential for building Debian packages.  This package also
 depends on the packages on that list, to make it easy to have the
 build-essential packages installed.
 .
 If you have this package installed, you only need to install whatever
 a package specifies as its build-time dependencies to build the
 package.  Conversely, if you are determining what your package needs
 to build-depend on, you can always leave out the packages this
 package depends on.
 .
 This package is NOT the definition of what packages are
 build-essential; the real definition is in the Debian Policy Manual.
 This package contains merely an informational list, which is all
 most people need.   However, if this package and the manual disagree,
 the manual is correct.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by 9400 on 2007-08-20
Wow, that was fast.  And I forgot, I'm running Feisty Fawn, 7.04.

Paul133 - I did have all the repositories enabled,  And I have bsh in Development, but I don't have byacc, either, just goes right to dbus after bsh.

taurus - sudo aptitude update is running right now.

logos34 - Yes, Main, Universe and Multiverse are all enabled in the Repositories menu.

---

### Post by 9400 on 2007-08-20
I have no idea what I did, but I clicked the reload button and there it is.  No idea how, but I've got it.  Thanks for the help.

---

### Post by taurus on 2007-08-20
Probably because you need to run the "update" first.

---

