---
title: "will MOL run on Intrepid?"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-11-21
Intrepid
uname -r returns: 2.6.25-2-powerpc
TiBook G4

I downloaded the deb for mol-drivers-osx from:
[http://packages.debian.org/unstable/otherosfs/mol-drivers-macosx](http://packages.debian.org/unstable/otherosfs/mol-drivers-macosx)

and just installed it with the installer. I had tried using the version in synaptic but it wanted to remove mol completely-not going to work.
The deb installed fine and I then tried to compile the modules for my kernel, as per the README in mol-source:
```
@ubuntu:/usr/src/modules/mol$ sudo make install
make -C /lib/modules/`uname -r`/build M=`pwd`/kmod
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make: [kmod] Error 2 (ignored)
make -C /lib/modules/`uname -r`/build M=`pwd`/netdriver
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make: [netdriver] Error 2 (ignored)
make INSTALL_MOD_PATH= -C /lib/modules/`uname -r`/build M=`pwd`/kmod modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make: [kmod-install] Error 2 (ignored)
make INSTALL_MOD_PATH= -C /lib/modules/`uname -r`/build M=`pwd`/netdriver modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-powerpc'
make: [netdriver-install] Error 2 (ignored)

```
so I wonder where the Makefile is and I discover that it is a link to
/usr/src/linux-headers-2.6.24-19-powerpc

Apparently the link can't be followed by make so what to do?

Are there any other ways to get MOL for OSX to run on Intrepid?

---

### Post by ubuntubrian on 2008-11-21
Oops! Scratch that.what I found is that the link is broken. Its target is:
/linux-headers-2.6.25-2/Makefile 
but being on powerpc I can only find:
/linux-ports-headers-2.6.25-2/Makefile

Is this a simple matter of changing the link? How do I do this if this is so?

---

### Post by ubuntubrian on 2008-11-21
And in fact all of the links in the directory are broken in the same manner.

---

### Post by Leslie Viljoen on 2008-11-21
I tried hard to install MOL on Intrepid. I can't remember how I got the kernel source and the mol-drivers-osx to play together, I think I moved mol into the kernel source under modules somewhere. 

But anyway, once you get there, mol-drivers-osx doesn't compile. It is in the middle of being 'ported' for some reason. You'll see init.S won't compile with the GNU assembler.

I asked if it would help to unroll the offending macros, but my question about it has not gotten any response yet:
[http://sourceforge.net/mailarchive/forum.php?thread_name=f204810a0811160041h5a6e927et1be6bd475ec4db4a%40mail.gmail.com&forum_name=mac-on-linux-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=f204810a0811160041h5a6e927et1be6bd475ec4db4a%40mail.gmail.com&forum_name=mac-on-linux-devel)

Ubuntu bug (init.S won't compile):
[http://www.google.co.za/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=HbJ&q=mol+init.S&btnG=Search&meta=](http://www.google.co.za/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=HbJ&q=mol+init.S&btnG=Search&meta=)

---

### Post by Leslie Viljoen on 2008-11-21
In other words, no, MOL won't run on Intrepid. It looks as though the old version that I ran fairly well on Gutsy is being completely rewritten and is not ready yet.

---

### Post by ubuntubrian on 2008-11-21
I sure loved it when I was running Dapper. Unfortunately i upgraded before I realized the problem. Ah well!

---

### Post by mfox on 2008-11-21
It didn't run on Hardy either.  It was for this reason I removed Ubuntu from my PowerBook G4 and installed Debian Lenny instead.  The Debian and openSUSE developers made the necessary modifications to allow it to run on the newer kernels.  One hopes that the developers handling PPC Ubuntu will eventually pick it up.

---

### Post by ubuntubrian on 2008-11-22
I'd be interested in further discussion on Debian. I had it installed on my G3 Powerbook for a while. Does it run Gnash well as a plugin?

---

