---
title: "There's no Ubuntu version of the latest Pidgin! :("
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2007-12-31
I went to the Pidgin website and I saw this: 

[IMG]http://img205.imageshack.us/img205/2415/snapshot1ug0.png[/IMG]

WHAT? No Ubuntu or Debian package. Confuzion!

---

### Post by Perfect Storm on 2007-12-31
Try getdeb: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)
Or download the source code to compile

---

### Post by Ub1476 on 2007-12-31
You can always compile it, but I don't think there are any special change since it isn't in backports. 

To compile, extract the tar.gz file (source), open it in a terminal (cd foldername) and write:

```
./configure
make
sudo make install
```

I guess the latest version will get on getdeb.net soon too though.

---

### Post by zipperback on 2007-12-31
> **EleFlameMax said:**
> I went to the Pidgin website and I saw this: 

[IMG]http://img205.imageshack.us/img205/2415/snapshot1ug0.png[/IMG]

WHAT? No Ubuntu or Debian package. Confuzion!


You can install pidgin from the repositories.
sudo apt-get install pidgin

If the version available is not the most recent one, then download the source code for it from the website and just build it.

Here is the link to the source code page for it.
[http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

- zipperback
:popcorn:

---

### Post by SOULRiDER on 2007-12-31
Theres a nice thread on the Howto forums on how to compile it from source. You could do that or ask anyone that has compiled it to send you their compiled package for you to install.

---

### Post by juniah on 2007-12-31
Doesn't apt-get have it?

```

sudo apt-get install pidgin

```

---

### Post by SOULRiDER on 2007-12-31
> **juniah said:**
> Doesn't apt-get have it?

```

sudo apt-get install pidgin

```

Thats an older version, several versions older i believe. You have to compile the latest or wait until hardy comes out.

---

### Post by juniah on 2007-12-31
Ah, didn't know this.

Thanks!

---

### Post by Sef on 2007-12-31
> Thats an older version, several versions older i believe. You have to compile the latest or wait until hardy comes out.

Because Ubuntu is a time released distro, software is usually not updated except for security patches.  You either have download it from another repository or through the backports which are open after the next version of Ubuntu comes out.

---

### Post by anthonie on 2007-12-31
I used to run GAIM and after upgrading to Gutsy I ended up with Pidgin, so it seems available.

---

### Post by SOULRiDER on 2007-12-31
> **anthonie said:**
> I used to run GAIM and after upgrading to Gutsy I ended up with Pidgin, so it seems available.

But the one in the repos isnt the LATEST version of pidgin

---

### Post by juniah on 2007-12-31
I think that the solution here is to either use the one in the repos (which is what I use) or to compile it.  For simplicity I say get the repos since its a oneline command.  Possibly an upgraded Pidgin will come with Hardy?

---

### Post by LowSky on 2007-12-31
hardy will have the newest version availible when it comes out. Every new version of ubuntu has updated software. check google for a .deb of the new version if your afraid of code.

as for the confusion of this thread ubuntu gutsy ships with 2.2.1
while [http://www.pidgin.im/](http://www.pidgin.im/)   has 2.3.1 availible


edit: get-deb has the 2.3.0 availible in 3 easy deb files

[http://www.getdeb.net/release.php?id=1855](http://www.getdeb.net/release.php?id=1855)

---

### Post by SOULRiDER on 2008-01-01
> **LowSky said:**
> 
edit: get-deb has the 2.3.0 availible in 3 easy deb files

[http://www.getdeb.net/release.php?id=1855](http://www.getdeb.net/release.php?id=1855)

I was just gonna say that, they have a nice selection of deb files ready to install. In fact, i think they even got a repo which is even better.

---

### Post by kevdog on 2008-01-01
Compiling from source on gutsy is actually pretty easy. Im always nervous about third party repositories, particularly things from getdeb.  

Its pretty easy to compile if you have compiled anything before.  You need the build-essential, linux-headers`uname -r` and pidgin dependency packages.  Download the latest tar.gz pidgin source, extract it, and then ./configure, make, sudo make install.  Thats about it.  

As an added bonus, if you know how to compile, you can further download and compile and install the purple-plugin-pack (for pidgin -- tons of cool pidgin plugins) and otr (for encrypted messaging).

---

### Post by raspark on 2008-01-02
I had been waiting for an updated version, so my daughter could use MySpace IM through Pidgin.  Unfortunately, it seems once a new dist of Ubuntu comes out,the older versions don't get to upgrade packages to newer versions.

So, I tried downloading and installing it from source, following a thread on the forums here.  After five hours of trying, I can't get the old version to purge and the new version to install.  When I try to remove GAIM, synaptic also wants to remove ubuntu-desktop, something which I'm not going to do.  It seems silly to me to have to remove the whole desktop just to remove an old, unused program.

The system I'm using will not function well under 7.10, it's about all it can handle, and still be usable, with 7.04.  I'm only 6 months out of date on the dist upgrade path, but it would seem that I'm stuck here.

So, I've wasted half of my only day off for the week, trying to do something that should take a few minutes, and this is after months of waiting.  And people wonder why Linux isn't taking off on the desktop, with regular users.

---

### Post by ugm6hr on 2008-01-02
> **raspark said:**
>  When I try to remove GAIM, synaptic also wants to remove ubuntu-desktop, something which I'm not going to do.  It seems silly to me to have to remove the whole desktop just to remove an old, unused program.

The system I'm using will not function well under 7.10, it's about all it can handle, and still be usable, with 7.04.  I'm only 6 months out of date on the dist upgrade path, but it would seem that I'm stuck here.

You can just remove ubuntu-desktop.  It is not a "real" package, but just a container for all the default programs in Gnome/Ubuntu.  So if you want to remove *any* default programs, it insists on being removed too (because it won't allow its container to be missing any components).  Ubuntu itself will continue to run unharmed (as long as you don't use Synaptic to update to Gutsy).

As for the 7.10 vs 7.04 - there is no reason why they wouldn't run as well as each other (albeit without Compiz desktop effects in Gutsy).  The rumour is that Gutsy takes slightly longer to boot (about the same for me), but runs faster once loaded (agreed).  If you are going to do this - I'd recommend the fresh install rather than Synaptic upgrade.  Perhaps if things are a bit slow, you might like to try Xubuntu instead this time (or even a custom IceWM Ubuntu).

---

### Post by kd7swh on 2008-01-02
I just compile the latest builds of things. Most of the time they get updated in the repos. stream anyway. The six month cycle is really nice. It keeps my systems clean, and running smoothly.

---

### Post by thelatinist on 2008-01-02
> **raspark said:**
> I had been waiting for an updated version, so my daughter could use MySpace IM through Pidgin.  Unfortunately, it seems once a new dist of Ubuntu comes out,the older versions don't get to upgrade packages to newer versions.

This is not quite accurate.  It is more accurate to say that once a distribution is released most packages do not get upgraded to newer versions.  The way Ubuntu's versioning works, versions of applications in the repositories are frozen at release except for bug fixes and patches.  If a program has a major version upgrade, you have to install it manually or wait for the next release of Ubuntu.

> So, I tried downloading and installing it from source, following a thread on the forums here.  After five hours of trying, I can't get the old version to purge and the new version to install.  When I try to remove GAIM, synaptic also wants to remove ubuntu-desktop, something which I'm not going to do.  It seems silly to me to have to remove the whole desktop just to remove an old, unused program.

Ubuntu-desktop is basically just a list of packages to be installed that is used when doing a version upgrade of Ubuntu (i.e., feisty to gutsy) to ensure that you get all the latest default software.  Removing it will not remove any software from your system or change any settings.  Moreover, if you have no intention of upgrading from 7.04, you have absolutely no use for it.  Besides, if you later decide to upgrade you need only re-install ubuntu-desktop then.

---

### Post by kevdog on 2008-01-02
You do not need to uninstall GAIM or any previous versions of pidgin if you do not want to if you compile from source.

Usual ubuntu programs are installed into the base directory
/usr

Whereas compiled programs are installed into 
/usr/local

So the executable for gaim will most likely be in
/usr/bin

Whereas your compiled program will be in:
/usr/local/bin

You control this placement at the time of compiling when you specificy the prefix option:
./configure --prefix=(path)

By default if you do not use the --prefix option it will be placed into /usr/local.  I would not change this setting.

Can you be more specific why it will not install.  If you compile from source and  at the conclusion of the compilation, you type sudo make install, this process does not check for any previously installed package.  This method goes outside the apt or package management system.  Some people fear going outside the package management system, however in certain cases however it gives you a lot more control since it removes the checks such as wanting to uninstall various packages.

How are trying to install your compiled version?

Dont worry the first time you install pidgin its quite frustrating and takes a while.  Dont give up on it.  Last night I recompiled the latest version of pidgin, the pidgin plugins, and otr in about 1 hour.  The compilation on my old POS laptop takes about 30 minutes b/c its so SLOW.

---

### Post by hyper_ch on 2008-01-02
what about the backports? Isn't it in there?

---

### Post by kevdog on 2008-01-02
Pidgin just started being distributed in the Ubuntu repositories in Gutsy.  There are no backports available.

---

### Post by hyper_ch on 2008-01-02
well, backports from the hardy repos...

---

### Post by kevdog on 2008-01-02
That -- Im not sure about.  Im sure somebody may have done it.

---

### Post by r4ik on 2008-01-02
LowSky's link,

[http://www.getdeb.net/release.php?id=1855](http://www.getdeb.net/release.php?id=1855)

updates to 2.3.0 thats oke with me.

---

### Post by raspark on 2008-01-03
> **ugm6hr said:**
> You can just remove ubuntu-desktop.  It is not a "real" package, but just a container for all the default programs in Gnome/Ubuntu. 

I thought this too a few years ago, when this was a test system for me. I did allow it to be uninstalled and it took me a couple days to recover back, because something did damage the install when that container was removed.  I'm loath to do it on a system that my wife depends on daily.

> **ugm6hr said:**
> As for the 7.10 vs 7.04 - there is no reason why they wouldn't run as well as each other (albeit without Compiz desktop effects in Gutsy).  The rumour is that Gutsy takes slightly longer to boot (about the same for me), but runs faster once loaded (agreed).  If you are going to do this - I'd recommend the fresh install rather than Synaptic upgrade.  Perhaps if things are a bit slow, you might like to try Xubuntu instead this time (or even a custom IceWM Ubuntu).

I moved to Xubuntu with Dapper because the system was so bogged down at that point.  Once Feisty came out, and I saw the recommended specs for Hardy, I decided that this sytem was at it's highest upgradable version.

Thanks, though.

---

### Post by Turin Turambar on 2008-01-03
Add this to the repo list:

deb [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main universe multiverse

key:
wget ubuntu.schmidtke-hb.de/aptrepository.asc
sudo apt-key add aptrepository.asc

They have Pidgin 2.3.1

---

### Post by raspark on 2008-01-03
I had a long reply already to go here and I lost it, timed log-out killed me on that one.  Suffice it to say that I'm not a novice, but nowhere near a guru.  I can accomplish most things on my own, and the rest with help from these forums.  I'm looking for a mainstream solution for the novice, so they don't get frustrated and head back to the M$ way.

---

### Post by raspark on 2008-01-03
> **Turin Turambar said:**
> Add this to the repo list:

deb [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) gutsy main universe multiverse

key:
wget ubuntu.schmidtke-hb.de/aptrepository.asc
sudo apt-key add aptrepository.asc

They have Pidgin 2.3.1

Thanks, I may play with this later.  Since it is pulling from a newer release, I have dependency conflicts to resolve.

---

### Post by raspark on 2008-01-03
> **kevdog said:**
> You do not need to uninstall GAIM or any previous versions of pidgin if you do not want to if you compile from source.

<<snip>>

Can you be more specific why it will not install.  If you compile from source and  at the conclusion of the compilation, you type sudo make install, this process does not check for any previously installed package.  This method goes outside the apt or package management system.  Some people fear going outside the package management system, however in certain cases however it gives you a lot more control since it removes the checks such as wanting to uninstall various packages.

How are trying to install your compiled version?

Dont worry the first time you install pidgin its quite frustrating and takes a while.  Dont give up on it.  Last night I recompiled the latest version of pidgin, the pidgin plugins, and otr in about 1 hour.  The compilation on my old POS laptop takes about 30 minutes b/c its so SLOW.

Sorry, but I can't be more specific.  After all that I had been through in trying to get the compile to work (it never did complete), I was totally frustrated and didn't keep any output.  I also did not intend to come into this thread and ask for help.  I was going to try again at a later date.

---

### Post by kevdog on 2008-01-03
Do you need instructions how to compile pidgin?

---

### Post by Perfect Storm on 2008-01-04
Ok, I finished how to compile Pidgin on Ubuntu 7.10 64-bit Gnome

[http://polarbeardk.blogspot.com/2008/01/build-pidgin-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2008/01/build-pidgin-from-source-710-64bit.html)

---

### Post by thelatinist on 2008-01-05
> **raspark said:**
> I thought this too a few years ago, when this was a test system for me. I did allow it to be uninstalled and it took me a couple days to recover back, because something did damage the install when that container was removed.  I'm loath to do it on a system that my wife depends on daily.

Take a look at the package.  All it does is make a whole bunch of things its dependencies.  There are no actual files in the package, and none should be uninstalled just by removing it.  I don't know what else you removed, but your problems can't have been caused by removing ubuntu-desktop.

---

### Post by machosos on 2008-01-05
i just tried it and it worked for me..thanks A.I.

---

### Post by Kosimo on 2008-01-05
No worries:

Getdeb has alread y the latest Pidgin Version:  2.3.1

[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)


First remove your installed pidgin

Open Terminal and type this:

> sudo apt-get remove pidgin


Then download that three debs, and install them following this order:

1- libpurple0
2- pidgin-data
3- pidgin


And everything is done ;)

---

### Post by Ghuloomo on 2008-02-17
so until now 3 solutions:
Compile the source (extract, ./configure, make, make install)
[get the latest version from getdeb ]("http://ubuntuforums.org/showpost.php?p=4078952&postcount=35")
[add that to the repo]("http://ubuntuforums.org/showpost.php?p=4063707&postcount=27")

I tried to go with the 1st one, coz I really want to get this solved. Not only pidgin, but any other programs i download and want to compile, this happens to me:
mohamed@ubuntu:~/pidgin-2.3.1$ make
make: *** No targets specified and no makefile found.  Stop.
mohamed@ubuntu:~/pidgin-2.3.1$ make install
make: *** No rule to make target `install'.  Stop.
mohamed@ubuntu:~/pidgin-2.3.1$ 

Guys am I doing something wrong?

---

