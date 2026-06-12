---
title: "Gcc absent from live cd installation----how to get a gcc compiler ?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-08
i have no  internet connection on my linux ubuntu 7.04 machine and i realy need the gcc compiler to install the multimedia codec.

i installed biuld-essential and g++ with synaptic from Live cd but isn't enogh.
i SAW the gcc compiler on the internet ,has 45 mega.

what should i do ? how to instal the gcc?
need burn it on a cd and then runing Synaptic on it?

?

---

### Post by jw5801 on 2007-10-08
In a terminal type:
```
sudo apt-get install gcc
```
Or else type "gcc" and hit enter and as well as returning a "bash: command not found" error, it should also tell you what package contains the program. If the issue is that you don't have an internet connection on your Ubuntu box and can't seem to find the package using the CD, you should be able to download it from [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gcc&sourceid=mozilla-search) and get it to your Ubuntu box that way.

---

### Post by bambubambu2 on 2007-10-08
i want to install from where you indicated but what Package?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gcc&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=gcc&sourceid=mozilla-search)

---

### Post by jw5801 on 2007-10-08
Well, as far as I'm aware the compiler should be included in build-essential. But if it's gone missing somewhere then I guess [that one](http://packages.ubuntu.com/feisty/devel/gcc). You'll also need at least the two dependencies that are listed (cpp and gcc-4.1), and their dependencies as well, as their dependencies dependencies. So this could quickly snowball. All of those should be in the build-essential meta-package though. What are you trying to do that's telling you you don't have gcc installed?

---

### Post by bambubambu2 on 2007-10-08
i have gcc ofcourse but are missing packeges ,so i downloaded a lot of sutuff, something like getlib,then il gcc ascked for another thing , and so on .
the last pack i installed was "bison",but now ask for another thing.

ok i'm realy stuff and pissed off.What should i do to install those god damn multimedia plugins ??

---

### Post by Beggar on 2007-10-08
> **bambubambu2 said:**
> i have gcc ofcourse but are missing packeges ,so i downloaded a lot of sutuff, something like getlib,then il gcc ascked for another thing , and so on .
the last pack i installed was "bison",but now ask for another thing.

ok i'm realy stuff and pissed off.What should i do to install those god damn multimedia plugins ??

You were forced to install bison because of a dependancy? That doesnt make sense, Bison should be dependant on gcc (it is a parser generator, which generates C code..).  As for installing multimedia codecs, when you attempt to watch a movie hat needs a codec, feisty will pop up a dialog which will allow you to download and install the codecs. Otherwise you will need to 

```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by MarkieB on 2007-10-08
there's a package called gcc-4.1 in synaptic, it usually suggests all the necessary additional packages..

---

### Post by Terl on 2007-10-08
> **bambubambu2 said:**
> i have gcc ofcourse but are missing packeges ,so i downloaded a lot of sutuff, something like getlib,then il gcc ascked for another thing , and so on .
the last pack i installed was "bison",but now ask for another thing.

ok i'm realy stuff and pissed off.What should i do to install those god damn multimedia plugins ??

Just get these:  [ubuntu-restricted-extras]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=feisty&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=ubuntu-restricted-extras&searchon=names").  These are most of the codecs you will need and then some.

I understand you getting frustrated but without an internet connection it is difficult to get all the packages.  Synaptic will do all the checking for you and grab the dependencies for you.  If you are doing this from another pc, you will have more manual checking to do to make sure you grab all the packages you need.

The other option, is to use an online retailer that sells these packages on dvd.  Yes, they will go out of date but you would at least have something.

---

### Post by christhemonkey on 2007-10-08
I would use [wubdepends]("http://wubdepends.sourceforge.net/").

You can run it on another pc to get a program and all its dependencies.

Then you should have a full set of .deb files to install.

---

