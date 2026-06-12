---
title: "Create your own meta packages question"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by rcpettit on 2006-01-02
I've searched all over the web for a how-to or tutorial on making your own meta packages with no luck.  The only thing I could find was for RH based distributions. I installed equivs but no luck so far.  I'm building a test system and want to use a meta package to automate the installation so I don't have to keep reinstalling the system from scratch again.

Thanks.

---

### Post by xtacocorex on 2006-01-03
I know that checkinstall will make .deb packages for (K)Ubuntu.

I'm not sure exactly how you can do this, but you could always download kubuntu-desktop, not install it and then look through the package to see how it works to get a feel for making your own meta-package.

Downloading and not installing with apt-get:
```

sudo apt-get install -d kubuntu-desktop

```
Just make sure /var/apt/cache (can't fully remember the location) is cleaned out before you look at kubuntu-desktop and will only show the one package when you download it.
```

sudo apt-get autoclean

```

I'm also not sure of how to search through the package, but I'm sure a read through dpkg's man pages might help. I do know that seaching inside a package is possible.

There might be some stuff that isn't listed because I haven't done this; this is just what I would start with if I was going about attempting this.

EDIT:
I did find this through a quick google search: [http://ubuntuforums.org/showthread.php?t=6221](http://ubuntuforums.org/showthread.php?t=6221)

I'm now intrigued about making a meta-package because I found a use for it, combining the Intel FORTRAN compiler and debugger into one file, once I fix the bug it has with the scripts when I made the two .deb packages.

---

