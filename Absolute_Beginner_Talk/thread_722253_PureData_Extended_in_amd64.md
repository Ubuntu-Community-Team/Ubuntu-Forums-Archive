---
title: "PureData Extended in amd64"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by regomodo on 2008-03-12
Has anybody got pd-extended to work in Ubuntu amd64? I can get it to work in Debian Etch amd64 by --force-architecturing the i386 package. I just can't get it to work in Ubuntu and is driving me up the wall.

```
pd: error while loading shared libraries: libjack.so.0: cannot open shared object file: No such file or directory
```

---

### Post by regomodo on 2008-03-15
i guess nobody uses it in Ubuntu then

---

### Post by jimqode on 2008-04-20
I also tried to get it to work on ubuntu hardy x64 to use with arduino. I was able to get as far as running the pd binary. But extensions don't work because of library version conflict. So it is useless. I think I'll switch to 32-bit version. 
If you are still watching this topic please tell me what you did.

---

### Post by hihihi on 2008-06-19
has anybody an idea where to get working pd-extended for 64bit?

did anybody tryed to install it via "get-libs"?

[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

seems like we are endangered species under the ubuntusers... :(

---

### Post by hihihi on 2008-06-19
i compiled it myself from source and it works perfect, nothing else needed so far..

[B][I]edit 3 weeks later:
I discovered that I just had compiled pd and not pd-extended, because i compiled in the wrong folder and had no clue how to do it right.[/I][/B]

---

### Post by ing.ajmv on 2008-07-09
Download the source...
example... Pd-0.39.3-extended.tar.bz2

```
tar xvf Pd-0.39.3-extended.tar.bz2
cd Pd-0.39.3-extended/pd/src
sudo autoconf
```

... this generate the "configure" file, then ...

```
./configure
sudo make
```

be careful with dependencies, maybe tk and tcl (dev packages) is needed

```
sudo make depend # optional
sudo make install
```

I'm not testing at all
sorry, my English is poorly

---

### Post by hihihi on 2008-07-10
> **ing.ajmv said:**
> Download the source...
example... Pd-0.39.3-extended.tar.bz2

```
tar xvf Pd-0.39.3-extended.tar.bz2
cd Pd-0.39.3-extended/pd/src
sudo autoconf
```



i think that by doing this, you will just compile the pd-src, but not the extended one...
so you end up with a normal pd installation and you'll have to compile the rest by yourself (externals).

---

### Post by hihihi on 2008-07-15
to compile pd-extended, you need to follow those instructions:

[http://puredata.info/docs/developer/Debian](http://puredata.info/docs/developer/Debian)

later, those could be helpful too:

[http://puredata.info/docs/developer/PdExtendedBuildSystem](http://puredata.info/docs/developer/PdExtendedBuildSystem)
[http://puredata.info/docs/developer/](http://puredata.info/docs/developer/)

and at the end those inside: ../Pd-0.XX.X-extended/packages/linux_make/README where very useful.

unfortunately the libdir loaders of 0.40 version won't compile,
pidip, OSCx and other externals won't compile neither, so I ended up hacking the Makefile in  ../Pd-0.XX.X-extended/externals and  ../Pd-0.XX.X-extended/packages.
At the end I had a succsesful installation, but as the compilation of libdir failed, all the externeals couldn't load, leaving me with a normal Pd / Gem / Pdp installation, basically. I tried to compile libdir against the former version "Pd-0.39.3-extended", and that worked. the compiled libdir.pd_linux however was not accepted by Pd-0.40.0-extended.
compiling Pd-0.39.3-extended's libdir.c against Pd-0.40.0-extended.spew out the same errors as before.
So, for me, it does not work...

---

### Post by hihihi on 2008-07-15
Hello there [working solution],

I ended up again removing the whole thing and followed the instructions of myo, here:
[http://puredata.hurleur.com/viewtopic.php?pid=8406#p8406](http://puredata.hurleur.com/viewtopic.php?pid=8406#p8406)
(thanks myo),
followed this "howto install 32-bit .deb packages on 64-bit":
[http://www.unixtutorial.org/2008/03/ins](http://www.unixtutorial.org/2008/03/ins) &#8230; on-64-bit/
and this one about how to install missing 32-bit libs using getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

some packeges couldn't be found by apt-get, so I had to get them here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
by typing the missing libs in the searchfield,
downloading the i386 versions,
opening those .deb packages with "Archive Manager" and browsing to data.tar.gz/./usr/lib/
selecting all the files and extracting them to /usr/lib32/

this worked pretty good.
pidip is working,
all externals are loaded,

works very nice :)

---

