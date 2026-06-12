---
title: "[SOLVED] Unable to compile Wine from source"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-21
I'm trying to compile Wine from source per [these directions]("http://www2.ambientdesign.com/forums/viewtopic.php?t=9634"), and I'm unable to do so.  The installer quits on me, throws out some output and told me to check the config.log file; which of course makes no sense to me at this early stage in my life with Linux :)

I was wondering if someone might be able to tell me what I need to do to get it to work correctly?  Here's the log file.

---

### Post by smartboyathome on 2008-01-21
Why compile it from source when there is a repo that is up to date for ubuntu?

---

### Post by Kilz on 2008-01-21
[This page will show you how to install wine with synaptic.]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by glotz on 2008-01-21
[QUOTE=smartboyathome]Why compile it from source when there is a repo that is up to date for ubuntu?[/QUOTE]
For performance. It could go the extra mile often needed in such emulated environments.

Quote from the config.log: "configure:2692: error: C compiler cannot create executables"
Do you have the build essentials? sudo apt-get install build-essential

---

### Post by emarkd on 2008-01-21
Have you successfully build software from the source before?  If not, have you installed the build-essential package?

---

### Post by toastysquirrel on 2008-01-21
> **smartboyathome said:**
> Why compile it from source when there is a repo that is up to date for ubuntu?
The link I got the suggestion from said that compiling Wine from source is what fixed the pressure sensitivity of his Wacom pad when used in ArtRage 2 (in Wine).  That's the only reason I'm trying to mess with this; up until this morning I had Wine installed from a repo without any problem.

> > **emarkd said:**
> Have you successfully build software from the source before?  If not, have you installed the build-essential package?

> **glotz said:**
> For performance. It could go the extra mile often needed in such emulated environments.

Quote from the config.log: "configure:2692: error: C compiler cannot create executables"
Do you have the build essentials? sudo apt-get install build-essential

No, I haven't got that; therefore I'm on my way to install it right now.

Thanks, I'll see if that does it! :)

---

### Post by toastysquirrel on 2008-01-21
Okay, I think I'm almost there.  Here's the new output I'm getting :p

```
Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

```

I'm guessing I need something that has to do with "X" and "flex"?

Whatever those are :-?

---

### Post by tht00 on 2008-01-21
> **toastysquirrel said:**
> Okay, I think I'm almost there.  Here's the new output I'm getting :p

```
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

```

I'm guessing I need something that has to do with "X" and "flex"?

Whatever those are :-?

That's odd that it isn't seeing X.

So far as flex, just install that through apt-get or Synaptic.  Then try it again.

---

### Post by emarkd on 2008-01-21
hrm, not sure on those, but if I were you, I'd:

sudo apt-get install flex

and see what happens

---

### Post by Kralizec on 2008-01-21
Thats an easy fix:

```

sudo apt-get install flex

```
will install that required flex package and that should solve that error. You'll probably get a few more errors like that one, just repeat the command above substituting 'flex' for the name of the missing package.

---

### Post by tht00 on 2008-01-21
> **glotz said:**
> For performance. It could go the extra mile often needed in such emulated environments.

Wine isn't considered emulation -- at least not in the traditional sense.

Plus, advantages of compiling packages for performance are mostly overstated (as opposed to precompiled binaries) -- especially for single packages.  You may notice performance gains when the entire system is customized, tweaked, and additional services/options are stripped... but for one package?  Pretty bogus.

BTW, I'm running Gentoo.  If there's any group of Linux users obsessive about performance, it'd be us. :)

---

### Post by glotz on 2008-01-21
Usually when compiling you also need the -dev package, so now it'd be flex-dev.
You can first take a look at what the package is all about with
apt-get show flex
and if you feel like installing it (and the dev pack too)
sudo apt-get install flex flex-dev

[QUOTE=tht00]Wine isn't considered emulation -- at least not in the traditional sense.[/QUOTE]
Yeah, GNU is Not a Unix. WINE Is Not an Emulator... :)

---

### Post by toastysquirrel on 2008-01-21
I installed Flex, then I noticed when it was checking for flex and whatnot it output:

[COLOR="Red"]x = no
flex = flex
bison = no[/COLOR]

So I grabbed bison, restarted the install and it looked like it was going to go through; but it didn't.  When it was performing similar checks like the above there were sever [COLOR="Red"]... no[/COLOR] thrown between [COLOR="Red"]... yes[/COLOR]. Then it finished with the following:

```
configure: libxml2 development files not found, XML won't be supported.
configure: libxslt development files not found, xslt won't be supported.
configure: libhal development files not found, no dynamic device support.
configure: lib(n)curses development files not found, curses won't be supported.
configure: libsane development files not found, scanners won't be supported.
configure: libgphoto2 development files not found, digital cameras won't be supported.
configure: liblcms development files not found, Color Management won't be supported.
configure: libldap (OpenLDAP) development files not found, LDAP won't be supported.
configure: libcapi20 development files not found, ISDN won't be supported.
configure: libcups development files not found, CUPS won't be supported.
configure: fontconfig development files not found, fontconfig won't be supported.
configure: OpenSSL development files not found, SSL won't be supported.
configure: libjpeg development files not found, JPEG won't be supported.
configure: libpng development files not found, PNG won't be supported.

configure: WARNING: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

configure: Finished.  Do 'make depend && make' to compile Wine.

Install the X development headers and try again.
```

Here's as much of the terminal output as I could copy (file included).  This is kinda cool in a weird, I don't quite know what I'm doing sort of way.

---

### Post by emarkd on 2008-01-21
Not sure, but I think those X11 headers are in the libx11-dev package..

---

### Post by emarkd on 2008-01-21
By the way, you can search through the repository from the commandline by running:

sudo apt-cache search *whatever*

If you need more information about a package before you install it, run

sudo apt-cache showpkg *whatever*

You can use these commands to find any of the other libraries you want/need before you compile your package

---

### Post by tht00 on 2008-01-21
> **glotz said:**
> Yeah, GNU is Not a Unix. WINE Is Not an Emulator... :)

Yeah... :)

> **emarkd said:**
> Not sure, but I think those X11 headers are in the libx11-dev package..

From a quick search, I found that it might be xlibs-dev... but I'm not positive on that.


> **emarkd said:**
> By the way, you can search through the repository from the commandline by running:

sudo apt-cache search *whatever*

If you need more information about a package before you install it, run

sudo apt-cache showpkg *whatever*

You can use these commands to find any of the other libraries you want/need before you compile your package

For a beginner, I recommend using the Synaptic interface.

---

### Post by toastysquirrel on 2008-01-21
> **tht00 said:**
> Yeah... :)



From a quick search, I found that it might be xlibs-dev... but I'm not positive on that.




For a beginner, I recommend using the Synaptic interface.
I would.... but, I have the added challenge of having my Ubuntu box offline.  I've been making use of [Nonetdebs ]("http://www.nonetdebs.homeip.net/")and it's been treating me well enough.

---

### Post by toastysquirrel on 2008-01-21
I Googled the term, "Install the X development headers and try again" and eventually it pointed to installing the **xorg-dev** package (which consists of around 78 dependencies :shock: ). I don't suppose having access to the Ubuntu DVD would help my situation out at all??

---

### Post by glotz on 2008-01-22
-

---

### Post by JoshuaRL on 2008-01-22
> **tht00 said:**
> BTW, I'm running Gentoo.  If there's any group of Linux users obsessive about performance, it'd be us. :)

:lolflag:

Toasty, I would say yes.  Try putting the DVD in and "apt-cache search"ing for whatever packages you think you need.  I believe all of the xorg stuff should be on the DVD.

Just because I'm curious, how do you not have an installer DVD?

---

### Post by zvacet on 2008-01-22
Go to the folder from wich you try to compile and type 

```
sudo make clean
```

That will clean what yoi did before.You don´t haver to be afraid to do that,because you will not lose anything.After that try this command

```
auto-apt run ./configure
```

---

### Post by toastysquirrel on 2008-01-22
> **JoshuaRL said:**
> :lolflag:

Toasty, I would say yes.  Try putting the DVD in and "apt-cache search"ing for whatever packages you think you need.  I believe all of the xorg stuff should be on the DVD.

Just because I'm curious, how do you not have an installer DVD?
I'm sure this question is ridiculous but, what's an "installer DVD"?  I used the LiveCD to install Gutsy, and then, per someone else's suggestion, I downloaded the [DVD ]("http://ubuntu-cdimage.datahop.it/releases/gutsy/release/")to use for picking up stray dependencies; which I have yet to utilize because I haven't figured out how to mount an .iso image as a virtual disk yet, only as a browseable folder.


> **zvacet said:**
> Go to the folder from wich you try to compile and type 

```
sudo make clean
```

That will clean what yoi did before.You don´t haver to be afraid to do that,because you will not lose anything.After that try this command

```
auto-apt run ./configure
```
I'm just curious what I should expect the above code to do and how will I know if it was successful?

After installing xorg-dev, Wine compiled - apparently - without a hitch.  However I don't have any shortcuts in the App menu :( so I was wondering if anyone knows what I need to do to get those back?

---

### Post by zvacet on 2008-01-22
> I'm just curious what I should expect the above code to do and how will I know if it was successful?

That command install dependencies and you know that is succesfull if there is no error after runing it.

---

### Post by rosegarden78 on 2008-01-22
Neither could I you may consider using WINE from the repositories works great for me.

---

