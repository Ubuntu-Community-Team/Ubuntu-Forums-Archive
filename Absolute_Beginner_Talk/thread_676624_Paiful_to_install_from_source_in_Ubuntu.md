---
title: "Paiful to install from source in Ubuntu"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by sundar22in on 2008-01-24
I am a Ununtu newbie. I want to install apps from source. I tried many times, but it seems that Ubuntu 7.04 does not come with all the necessary compilers and libraries for installing the app. I installed build essentials, even then I am unable to install any app from source.


Is there any how-to available for making Ubuntu 7.04 ready for building from source?

Thanks.

~ Sundar ~

---

### Post by jfinkels on 2008-01-24
If you post any specific error messages you get, we can help diagnose your problem. As for general info, take a look at the first link in my signature.

---

### Post by macogw on 2008-01-24
Why do you need to install from source?   Just about anything can be found in the repos.

Well, anyway, once you have build-essential, that's the compilers and autoconf and all, but different programs have different build dependencies (other things, like libraries and development headers, that have to be installed before they can be compiled).  If you're just compiling a newer version of something that's in the repositories (like to get more features), you can run ```
sudo apt-get build-dep <package>
``` to install all of the build-dependencies for that package.  Otherwise, you're going to have to see what ./configure complains about and look for a -dev package in Synaptic (System -> Administration -> Synaptic Package Manager...the usual way of installing advanced things, like developer tools, on Ubuntu...user applications can be found through Applications -> Add/Remove which is really just a simplified Synaptic) which matches what you need (or which the internet says the missing file belongs to).

---

### Post by Brunellus on 2008-01-24
installing from source is slightly beyond the scope of most 'absolute beginners,' but . . . 

If you absolutely, positively *must* run the absolute bleeding edge, you can compile your own.  It may be helpful to get the build-dependencies for a package:

sudo apt-get build-dep $PACKAGE

but that assumes $PACKAGE is on the repos (even if in an older version).

If you can get all the dependencies installed (one way or another), I recomment using 

checkinstall

instead of 

make install

checkinstall creates a standard .deb package, which is easier to keep track of.

You can also investigate apt-build.

---

