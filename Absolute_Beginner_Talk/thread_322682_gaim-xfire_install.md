---
title: "gaim-xfire install"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2006-12-20
I am new to linux and dont know how to install could someone help me first thing I need to install is xfire-gaim could someone tell me how to do it in detail

---

### Post by Ecthelion on 2006-12-21
>  	I am new to linux and dont know how to install could someone help me first thing I need to install is xfire-gaim could someone tell me how to do it in detail

I guess you are referring to [this]("https://sourceforge.net/projects/gfire/").

If you are using Breezy Badger or Dapper Drake, just download th correct .deb packag and then do
```
sudo dpkg -i */place to where you downloaded the package/*
``` 

*/place to where you downloaded the package/* 
=> for example /home/*username*/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb

If you are using Edgy Eft then you'll have to recompile it.
Download  	gaim-xfire-0.6.0.tar.gz
Untar it with your archive manager.
Run the configure file => ./gaim-xfire-0.6.0/configure
And then do 
```
make
```
Finally
```
make install
```

If you use Edgy and this doesn't work, please post the error messages and what you've done so far

---

### Post by RoboAlex on 2006-12-31
Hi.

I'm trying to install the Gfire plugin for edgy eft but am having problems.  I extracted everything and ran the configuration script.  By "do" I assumed you meant open terminal in that window, and I tried to "make" but got the error :

make: *** No targets specified and no makefile found.  Stop.

I'm probably doing something stupid with my absolutely minimal unix experience (total noob speaking) and would appreciate your help, thanks ahead of time

EDIT:  I should probably point out that I am using xubuntu

-Alex

---

### Post by Ecthelion on 2006-12-31
>  	Hi.

I'm trying to install the Gfire plugin for edgy eft but am having problems. I extracted everything and ran the configuration script. By "do" I assumed you meant open terminal in that window, and I tried to "make" but got the error :

make: *** No targets specified and no makefile found. Stop.

Are you sure the ./configure went fine?
Because that's where the problems should be...

For example: I tried to recompile and install it, just to know better how to explain it, and it turns out I have a problem because I have no ./include/gaim/ dir.
This is probably because I have "Gaim 2.0.0beta3.1" and that it installed otherwise than the stable gaim.
Or so I think.

Maybe it would help to read the "README" and the "INSTALL" files which are in the dir you downloaded (If you downloaded the source).
These explain in detail how you should install it.

I hope you can find the error.

---

### Post by RoboAlex on 2006-12-31
I just notice I hod completely ignored the error that I got when I tried to run the configure

alex@*******Laptop:~/Desktop/gaim-xfire-0.6.0$ open configure -- prefix=/usr 
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console

thats definitely not a good thing.

---

### Post by Ecthelion on 2007-01-01
> alex@*******Laptop:~/Desktop/gaim-xfire-0.6.0$ open configure --prefix=/usr
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console

:KS 

It's not that bad.
When I said run the configure script, I meant:
```
~/Desktop/gaim-xfire-0.6.0/configure --prefix=/usr
```

Or as they say in the README:
[QUOTE=README]4) Run the configure script.  use the prefix option to determine where to
install the software.  ./configure --prefix=/usr[/QUOTE]

I wouldn't be surprised if you have some errors when running the configure file. Please post them.
(If it's the first time you compile somthing you probably will have some errors)

---

### Post by CC=AC3 on 2007-01-29
Sorry for the bump. Am new here and this is my very first compile. I dont know what to make of these errors:

/usr/bin/install: cannot remove `/usr/lib/gaim/libxfire.so': Permission denied
make[2]: *** [install-pluginLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/bhuvic/Desktop/gaim-xfire-0.6.0/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bhuvic/Desktop/gaim-xfire-0.6.0/src'
make: *** [install-recursive] Error 1

Thanks in advance

-AC3

---

### Post by Ecthelion on 2007-01-30
> /usr/bin/install: cannot remove `/usr/lib/gaim/libxfire.so': Permission denied

This probably happened when you did
```
make install
```
??

If so then use
```
sudo make install
```
instead.

If not, please tell us which command gav that error... Can't really help you without knowing what command gives the error.

---

### Post by trill on 2007-01-31
im having issues too  :confused: 

dw@dscomp:~$ ~/Desktop/gaim-xfire-0.6.0/configure --prefix=/usr
cat: ./VERSION: No such file or directory
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SSL... yes
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Sqwishy on 2007-01-31
> **trill said:**
> im having issues too  :confused: 
...
No package 'gaim' found
 Well it looks like you're trying to install a gaim plugin when gaim isn't installed?

---

### Post by trill on 2007-01-31
Odd,because I'm using Gaim right now :confused:

---

### Post by Ecthelion on 2007-02-01
> 
 	Odd,because I'm using Gaim right now
It can happen that the gaim binary isn't found.
Read the INSTALL file:

> 
To Compile
==========

for gaim-xfire 0.6.0

This is a total rewrite of the plug-in.  We now require libssl or some ssl
library installed to function properly.  On debian based Linux distributions
please have the package libssl-dev installed as well as the gaim-dev package
installed.  **This single source tarball works with gaim 1.5 and gaim 2.0.0.**

* For gaim 2.0.0 users, this version was testing and known to work with
gaim 2.0.0beta3 and 3.1.

This package uses the auto-tools configure script process.  This makes
distributing and compiling applications on a wide variety of hardware easier.

By default ./configure will set the installation path of this gaim library
to /usr/local -- for most users this is NOT the correct directory.

* For most users, the --prefix option will be --prefix=/usr

**1) locate your gaim binary which will probably be /usr/bin/gaim**

2) locate the gaim header files installed with the dev package.  They are
usually installed in /usr/include/gaim.  If you have this directory and
there are many files that end in .h, then this is the directory you want.

3) using step 1 and 2 above determine the prefix to use as an option to
configure. If steps 1 and 2 are exactly what you see above, then your prefix
is --prefix=/usr, if perchance #1 and #2 were /usr/local/bin/gaim, and
/usr/local/include/gaim, then your prefix is --prefix=/usr/local


4) Run the configure script.  use the prefix option to determine where to
install the software.  ./configure --prefix=/usr

*ERRORS*  We check for required packages using pkg-config during the configure
script.  If these packages are not found you need to install them. We need:
	
	gaim.pc
	libssl.pc -or- openssl.pc

If the configure script complains about not finding the correct version of
gaim, you may need to pass --with-gaimversion= option to configure to set
it explicitly.  The valid options to --with-gaimversion are 1.5 or 2.0.  We
need to know what gaim version API to use during the compile.  We can
auto detect this by running gaim --version and trying to determine what
version you are running. However if your compiling this plugin for a gaim
version that is *not* the gaim binary in your path, you should read the
Advanced Compile options below.

5) make

6) as root, run make install

7) copy data/gfire_games.xml to your users .gaim/ directory.
This is where we now look for our game id to name translation.

8) use the data/gfire_launch.xml as an example of how to tell gaim-xfire what
games you can play and how to launch them to join games.  Read README.joingame
for more information.


PLEASE READ THE README, before running gaim with the new plug-in installed.





As you can read it only works with some of the gaim versions...

---

### Post by EvilMarshmallow on 2007-02-01
I have a fresh Ubuntu Edgy install and it works fine for me... it's not the gaim version that's killing it.

Edgy has gaim installed to a slightly different place from the "default"... it took me a few tries to get this working too.  I can't remember where it actually was but I think my prefix was /usr/bin.  Find the gaim executable and the path to it is what you need to use.

IIRC, You'll get no message that everything's fine when you run the config with the proper prefix... it just comes back to a command line without so much as a "Configure Complete".

After that you can run the sudo make install, etc.  Close gaim and then once you've installed reopen it and you should have the option for XFire when you create a new gaim account.

Good luck!

---

### Post by Sqwishy on 2007-02-01
Why are you compiling anyway? You can get the 32bit versions from
[https://sourceforge.net/project/showfiles.php?group_id=141362](https://sourceforge.net/project/showfiles.php?group_id=141362)
and a 64bit version from
[http://www.ubuntuforums.org/showthread.php?t=319605](http://www.ubuntuforums.org/showthread.php?t=319605)

---

### Post by Ecthelion on 2007-02-01
> **Sqwishy said:**
> Why are you compiling anyway? You can get the 32bit versions from
[https://sourceforge.net/project/showfiles.php?group_id=141362](https://sourceforge.net/project/showfiles.php?group_id=141362)
and a 64bit version from
[http://www.ubuntuforums.org/showthread.php?t=319605](http://www.ubuntuforums.org/showthread.php?t=319605)

If you would have looked more closely you would have seen there is no version for Edgy Eft,
only for dapper and breezy


@EvilMarshmallow: That's why I put this on fat on the document
**1) locate your gaim binary which will probably be /usr/bin/gaim** :cool:
They say to locate it... ;-)

---

### Post by EvilMarshmallow on 2007-02-01
Yeah, whoops, that came out wrong.  I'm not sure what my prefix ended up being but I remember that Edgy has gaim installed in a different place.  If you look, I said I thought my **prefix** was /usr/bin... when the readme recommends a prefix of /usr.

I know I did something just very slightly different from the readme to get it to work with Edgy.  Sorry for the confusing post.

---

### Post by Sqwishy on 2007-02-01
> **Ecthelion said:**
> If you would have looked more closely you would have seen there is no version for Edgy Eft,
only for dapper and breezy Oh what? But the one called  	gaim-xfire_0.6.0-gaim1.5-etch1_i386.deb is edgy isn't it? When i compiled mine in amd64 it was called gaim-xfire_0.6.0-gaim1.5-etch1_amd64.deb so i assumed that the etch1 thing was edgy or something. Maybe not, i've been wrong before...

---

### Post by trill on 2007-02-05
Actually,I found a .deb in the link you gave me that worked for Gaim 2.0 on edgy.  	 	gaim-xfire_0.6.0-g2.0b3-r2-ubuntu1_i386.deb

I don't know I missed it before,but it seems to work ok.

---

### Post by Sqwishy on 2007-02-05
> **trill said:**
> I don't know I missed it before,but it seems to work ok. You missed it? lol your special ^^ jk ... its good you found it

---

### Post by trill on 2007-02-05
Yes I am special! At least,that's what my mommy tells me.:) :)

---

### Post by iLemon on 2007-02-09
I think my problem is that I don't have dev packages for gaim installed.  I do not have a /usr/local/gaim directory.  When I try to configure I get the following error.  

 ./gaim-xfire-0.6.0/configure --prefix=/usr
cat: ./VERSION: No such file or directory
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

If this is the case, how do I install the libssl-dev and gaim-dev packages in 6.10 Edgy Eft?

---

### Post by EvilMarshmallow on 2007-02-09
iLemon,

The error message you're getting looks more like a permissions thing to me.  Did you have sudo before ./configure?

As for installing libssl and gaim-dev packages, go to synaptic and look them up.  They should be there.

---

### Post by iLemon on 2007-02-09
I did sudo at the beginning of the configure line, but didn't think to include it.

After discovering synaptic, I installed the dev packages.   Everything went well with configure, make, and make install.  xfire plugin is now running. :D

---

### Post by ZeroXR on 2007-02-11
Question... Does anyone know if there will be any Guild or Clan support for the GAIM-Xfire plug-in? Is there one that supports that?

---

### Post by EvilMarshmallow on 2007-02-11
What do you mean?  There was a "clans" feature in Xfire that was beta last fall... but it was never part of the client.  You managed it from their website... log in to your account and you could set up clans, invite others, etc.

---

### Post by ZeroXR on 2007-02-12
It's part of the Windows Client now, as I can see my friends, but my guild members are on the "Clan" section of my list.

---

