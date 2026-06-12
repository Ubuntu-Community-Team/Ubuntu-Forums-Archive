---
title: ":-? Failed to install BRL-CAD"
date: 2007-06-12
forum: Art &amp; Design
---

### Post by malacai on 2007-06-12
I've been trying, without success, to install BRL-CAD on my Ubuntu 7.04 Feisty Fawn distribution.
I am installing the 7.10.0 release of BRL-CAD from source and everything's fine until I run ./configure (which isn't very far at all).
I have all the neccessary releases of gcc, libtool, make, automake, autoconf, and have double-checked the INSTALL and README.Linux files.

Please helop, I'm a newb who's dearly in love with Linux so far, but I've hit the wall on this one.

Here's everything I've run since extraction to my failed attempt at ./configure.




.........
zippo@zippo-desktop:~$ cd ~/ext3/CAD/brlcad-7.10.0zippo@zippo-desktop:~/ext3/CAD/brlcad-7.10.0$ sh autogen.sh
Preparing the BRL-CAD build system...please wait

Found GNU Autoconf version 2.61
Found GNU Automake version 1.9.6
Found GNU Libtool version 1.5.22

Automatically preparing build ... done

The BRL-CAD build system is now prepared. To build here, run:
./configure
make
zippo@zippo-desktop:~/ext3/CAD/brlcad-7.10.0$ sh ./configure --enable-optimized --prefix=/home/zippo/ext3/BRL-CAD/
./configure: ./sh/shtool: /bin/sh: bad interpreter: Permission denied
************************************************** ********
*** Configuring BRL-CAD Release 7.10.0, Build 20070601 ***
************************************************** ********
./configure: ./sh/shtool: /bin/sh: bad interpreter: Permission denied
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking where BRL-CAD is to be installed... /home/zippo/ext3/BRL-CAD/
checking where BRL-CAD resources are to be installed... ${prefix}/share
checking whether dependency tracking should be enabled... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether a configure cache exists... not found
configure: *** Automatically caching to config.cache.linux-gnu.zippo-desktop ***
./configure: ./sh/shtool: /bin/sh: bad interpreter: Permission denied
checking ... a r g u m e n t s ... (1 of 9)
./configure: ./sh/shtool: /bin/sh: bad interpreter: Permission denied
checking for X11 in /usr/X11R6... found
checking for X11 in /opt/X11R6... not found
checking for X11 in /opt/X11... not found
checking for X11 in /usr/X11... not found
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
zippo@zippo-desktop:~/ext3/CAD/brlcad-7.10.0$
.........

---

### Post by maruchan on 2007-06-12
Do a forum search for this text:

```
/bin/sh: bad interpreter: Permission denied
```

...I did it and I came up with lots of leads that you should probably follow up on. I don't know which would be the specific problem, but there are lots of diagnostic-type one-liners that might be helpful...all sitting in the forum database. ;)

---

### Post by maruchan on 2007-06-12
BTW...is there a specific reason you're compiling from source? I [found a .deb]("http://sourceforge.net/project/showfiles.php?group_id=105292") on the project site...

---

### Post by john_3000 on 2007-08-04
If that's the same .deb I installed, for no good reason I can think of it was compiled with the -g debug option and therefore runs slowly.  The benchmark suite warns you about it.  

This (releasing debug code) happens all too often, in my experience.

---

### Post by MichaelSM on 2007-08-11
I installed  brlcad 7.8.4.deb the other day and can't find it. It isn't listed in Graphics. I tought I'd fudged it so tried again. The package is already installed. 

What's the terminal command? 

Thanks.

Mike.

---

### Post by maruchan on 2007-08-11
I think the command is "mged".

---

### Post by MichaelSM on 2007-08-13
Thank you for that, Maruchan. mged  didn't work but it set me looking around a bit more.

Turns out the brlcad deb package is a bit weird and anyone who reads this post should think about compiling brlcad themselves from the tar package on the brlcad site. 

By typing in 'brlterm' in console, another console window opens up, and then one can type in 'mged' there. That at least gets one into what looks like a brlcad window.

I haven't taken it any further than that unfortunately.

Hope this helps someone.

Cheers,
Mike.

---

### Post by cb951303 on 2007-08-13
I use the 7.10.0 deb and it's not slow at all....

---

### Post by MichaelSM on 2007-08-13
Thanks. I'll find that version and install it. I was using 7.8.4 from memory.

Cheers, Mike.

PS Just searched. Where did you find the 7.10.0.deb ?

---

