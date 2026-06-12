---
title: "&quot;make&quot; not working?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by loserboy on 2006-12-11
hey i'm trying to learn more about installing stuff from command line and move away from the synaptic interface but i'm having a problem with installing a new version of gnomesword.

```
mike@mike-desktop:~/Desktop/gnomesword-2.1.10$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... no
mike@mike-desktop:~/Desktop/gnomesword-2.1.10$ make
make: *** No targets specified and no makefile found.  Stop.

```

make isnt working and i dont know enough to tell why, I see a makefile in the folder (makefile.in and makefile.am).
anyway if someone could tell me what to do and also what to look for in the future that would be cool, thanks
also i'm running gnome why does it say "checking for GNOME... no"

---

### Post by jonny123 on 2006-12-11
There's no makefile in directory that looks like it. look for 'makefile'

---

### Post by K.Mandla on 2006-12-11
Did you install build-essential? The compilation programs are lumped together and are not installed by default. I'm pretty sure "make" is one of them.

---

### Post by Sqwishy on 2006-12-11
> **loserboy said:**
> hey i'm trying to learn more about ```
mike@mike-desktop:~/Desktop/gnomesword-2.1.10$ ./configure
checking for gawk... no
checking for GNOME... no

``` make sure you have those.

> **loserboy said:**
> 
also i'm running gnome why does it say "checking for GNOME... no" thats wierd? maybe check their web site, it probobly requeres certain libraries, check 'gnome' in synaptic. make sure it' installed

---

### Post by taurus on 2006-12-11
You need Gnome development package if you plan to compile something for Gnome.  Use synaptic and search for it...

---

### Post by loserboy on 2006-12-11
ok ill do all that and get back to you... strange i kinda thought that stuff would be pre-installed, seems like a pretty standard task

---

### Post by taurus on 2006-12-11
Not the development packages...

---

### Post by loserboy on 2006-12-11
ok i installed build-essential, did ./configure againn then "make" same output though, also i know theres a makefile i'm lookin right at it

Edit: do i need to restart x or anything?

---

### Post by taurus on 2006-12-11
So, did you install the development package for Gnome?

---

### Post by loserboy on 2006-12-11
would it just be called  gnome-dev or something  ill go look for it now

---

### Post by taurus on 2006-12-11
Yip.  Something like that!  Otherwise, just use gnome and look the the ones with "-dev" in there...

---

### Post by loserboy on 2006-12-11
lol wow there is alot of gnome-dev-* and such...

i hate to be a pest but....you think you could narrow it down for me

so far i see gnome-applets-dev, gnome-core-devel and  gnome-devel they all have plausible information in them so i cant decide

---

### Post by taurus on 2006-12-11
Gnome-devel should include the gnome-core-devel so use aptitude for better dependencies...

```
sudo aptitude update
sudo aptitude install gnome-devel
```

---

### Post by loserboy on 2006-12-11
I know this is taking up way more time than it should but i appreciate u hanging in here with me :)

```
mike@mike-desktop:~/Desktop/gnomesword-2.1.10$ dir
ABOUT-NLS     configure.in              INSTALL              missing
acconfig.h    COPYING                   install-sh           mkinstalldirs
aclocal.m4    COPYING-DOCS              intltool-extract.in  NEWS
AUTHORS       depcomp                   intltool-merge.in    pixmaps
ChangeLog     doc                       intltool-update.in   po
config.guess  gnome-doc-utils.make      ltconfig             README
config.h.in   gnomesword.desktop.in.in  ltmain.sh            src
config.log    gnomesword.spec           m4                   TODO
config.sub    gnomesword.spec.in        Makefile.am          ui
configure     help                      Makefile.in

```

in the mean time i just wanted to make sure what im looking at is a makefile

---

### Post by loserboy on 2006-12-11
haha ok thanks the ./configure got past that step but now says

> checking for SWORD... no


i installed the only dev/lib packages i could find having to do with sword... you think maybe i should contacnt the gnomesword guys?

---

### Post by taurus on 2006-12-11
Did you install the -dev package for sword as well?  Either in README or INSTALL would tell you what you need to have on your machine before you can build it...

Otherwise, check on their website for all the required dependencies!

---

### Post by loserboy on 2006-12-11
yep installed everything related to it, i'm gonna hop over to their site.

still you helped me understand how the basics work and i thank you for it.

---

### Post by taurus on 2006-12-11
And if they happen to have a .deb for Ubuntu, that would even be better because you just install it with dpkg...

---

### Post by Schlomy on 2006-12-19
Hi! I'm having the same problem with configuring LAME, where it doesn't make the "Make" file. Everybody talkes about the "development package" for Gnome, but when I search Synaptic for this, there is no such package. When I search for Gnome, the only -dev packages are these:

libglade-gnome0-dev
libgnomebt0-dev
libgnome-pilot2-dev
libmimedir-gnome0-dev

Where is the development package?

Peace!

---

### Post by jpkotta on 2006-12-19
> **Schlomy said:**
> Hi! I'm having the same problem with configuring LAME, where it doesn't make the "Make" file. Everybody talkes about the "development package" for Gnome, but when I search Synaptic for this, there is no such package. When I search for Gnome, the only -dev packages are these:

libglade-gnome0-dev
libgnomebt0-dev
libgnome-pilot2-dev
libmimedir-gnome0-dev

Where is the development package?

Peace!

Do you need GNOME for LAME?  I wouldn't think that you would.  Anyway, try ```
sudo apt-get build-dep lame
```  Remember, you can just install LAME straight from the repos, no need to compile.  If you're compiling to optimize, then have a look at ```
man gcc
``` and set CFLAGS to something like "-march=pentium4 -O2 -mmmx -msse -msse2 -malign-double -mfpmath=sse".  YMMV.

---

