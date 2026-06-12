---
title: "Fresh 7.10 install can't compile"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by jackal242 on 2008-04-16
I just installed 7.10 on a host, downloaded the ffmpeg source code, ran ./configure and I get the following error:

root@hazard:/home/jackal/ffmpeg# ./configure 
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.


My gcc version is :
root@hazard:/home/jackal/ffmpeg# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

---

### Post by Het Irv on 2008-04-16
Do you have "build Essential" installed?  I don't know if that is your problem but it is somthing to check.

---

### Post by Paqman on 2008-04-16
Have you installed [build-essential](apt:build-essential)

---

### Post by jackal242 on 2008-04-16
root@hazard:/home/jackal# apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

---

### Post by eriqjaffe on 2008-04-16
It's build-essential, not build-essentials.

---

### Post by stchman on 2008-04-16
> **jackal242 said:**
> I just installed 7.10 on a host, downloaded the ffmpeg source code, ran ./configure and I get the following error:

root@hazard:/home/jackal/ffmpeg# ./configure 
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.


My gcc version is :
root@hazard:/home/jackal/ffmpeg# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Ubuntu has all the multimedia CODECs in it's repositories.

```
sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

I can play any audio or video out there, more that I could on Windows.

That being said, if you wish to compile programs in Ubuntu you need build-essential installed.

```

sudo apt-get -y install build-essential
```

---

