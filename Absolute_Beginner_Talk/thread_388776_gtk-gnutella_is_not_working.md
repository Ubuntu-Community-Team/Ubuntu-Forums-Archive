---
title: "gtk-gnutella is not working"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-03-19
so, i tried using gtk-gnutella, and it's just not working.  i found out that it's disabled from running.  Is there a new version i can install? without compiling something?  Perhaps a package? or mabey they are going to release a package so i wont have to?

---

### Post by Kateikyoushi on 2007-03-19
What do you mean with it's disabled from running ?

---

### Post by blendmaster on 2007-03-19
On the Gnutella network, which P2P file-sharing program are you using?

A while back, Frostwire had a problem in which it wouldn't connect to the network. However, a recent update has fixed this issue. Perhaps if you're using Frostwire yourself, you might want to try and update your version.

---

### Post by postmessages on 2007-03-26
Quite a few people are having this problem with gtk-gnutella. The version you'll have installed will most probably be 0.96.1 which is now over a year old. gtk-gnutella will refuse to work if it is more than a year old (although you can get it to work with some tweaking). The people who maintain the ubuntu repository haven't uploaded the new version (0.96.3, which came out in nov 2006) so, if you want to use the new version you'll have to compile it from source (it's not that hard, honestly!)

download the source file from [http://sourceforge.net/project/showfiles.php?group_id=4467](http://sourceforge.net/project/showfiles.php?group_id=4467)

it's zipped using bzip2 so unzip it using bunzip2.
un-tar it using "tar -xvf file-name"
navigate to the place where you've put the files (should be in your home dir.)
run the script ./Configure. This will ask alot of questions, just accept the defaults.
run "make". this will compile all the files for you!
as root, run "make install". this will install the files into the system for you.

then you're done!

if you can't be bothered to do this then run gtk-gnutella from a terminal and it will print some error messages and tell you it's too old. it will also tell you how to get it to work: you have to change the variable ancient_version_force in your config file (it tells you where it is). then it will work as normal.

---

### Post by Resurrection on 2007-03-27
For reference, the above post solution of compiling the newest version of gnutella does not work on Ubuntu.  It says at the end of the errors that it needs libxml2 installed, and even with it installed, it still gives the same error.

You can accept all the default compile options by using Configure -d.  Even this asks a weird question about a compiler compiler (yes that is typed twice intentionally) with the word (yacc) afterwards.  You must input something here, but not sure what.  No default choice is presented.

There is also a specific install.debian file which talks about debian systems, but that doesn't work either.

So unless I am the only one doing something wrong, the simple compile won't happen.

---

### Post by RagingAardvark on 2007-03-27
sudo apt-get install libxml2-dev

Does the trick.

---

### Post by lloyd_b on 2007-03-27
> For reference, the above post solution of compiling the newest version of gnutella does not work on Ubuntu. It says at the end of the errors that it needs libxml2 installed, and even with it installed, it still gives the same error.

You can accept all the default compile options by using Configure -d. Even this asks a weird question about a compiler compiler (yes that is typed twice intentionally) with the word (yacc) afterwards. You must input something here, but not sure what. No default choice is presented.

There is also a specific install.debian file which talks about debian systems, but that doesn't work either.

So unless I am the only one doing something wrong, the simple compile won't happen.

As noted, you need the "libxml-dev" package installed. 

As for the "yacc" question, just type "yacc" - this option is only required for some developers, so it doesn't matter what you type.

I recommend running "./Configure -Oders", as this will provide good answers automatically to everything except that stupid "yacc" question (note: that issue has been posted to the developers mailing list).

That said - if you want to avoid compiling, a .deb for 0.96.2 can be found at:
_[SourceForge]("http://sourceforge.net/project/showfiles.php?group_id=4467")_

A .deb for 0.96.3 can be found at:
_[ftp.unixdev.net]("http://ftp.unixdev.net/pub/debian-udev/pool/main/g/gtk-gnutella/")_

Lloyd B.

---

### Post by Resurrection on 2007-03-29
Nope.  I still get cannot compile against Gtk and glib errors.  Will try the deb, although the one referenced earlier in this thread didn't work either.  

By the way, I did read all the readme files and documentation in the source code, and I think they are pretty hosed.  The strongpoint of OSS is that if you read the documentation, you should be able to compile, and little mistakes like stating you need libxml2 when your really need libxml2-dev are pretty damn annoying.

---

### Post by lloyd_b on 2007-03-30
> Nope. I still get cannot compile against Gtk and glib errors. Will try the deb, although the one referenced earlier in this thread didn't work either.

If you post then actual errors, then we can probably figure out why it won't compile.

> By the way, I did read all the readme files and documentation in the source code, and I think they are pretty hosed. The strongpoint of OSS is that if you read the documentation, you should be able to compile, and little mistakes like stating you need libxml2 when your really need libxml2-dev are pretty damn annoying.

"libxml2" and "libxml2-dev" are actually two pieces of a single project.  The Debian (and Ubuntu) packagers decided that the development headers (the "-dev" package) should be distributed separately from the actual library.  

There are *hundreds* of projects that have been divided in this fashion.  So, as a rule, if you're compiling from source, and the docs say you need a particular package, with Ubuntu (or any Debian derivative) you should automatically install the associated "-dev" package as well as the main package.  I suspect that the same is true on most other Linux distros.

But Gtk-Gnutella isn't tied to Linux - that program runs on just about any Unix variant (Linux, BSD, Solaris).  So when they specify that you need "libxml", it's left up to you to figure out how to install that on your particular platform.

Lloyd B.

---

### Post by Resurrection on 2007-04-03
I understand what you are saying, however, if the documentation was better, I would not have to intrinsically know such a thing about -dev.  Like I said, its just quite annoying when the stereotype of a linux guru is someone who will tell you to "read the documentation" and when you do so, the poorly written docs don't help.  I never really liked this program anyway, so I have given up on it.

---

### Post by Adramelech on 2007-04-03
The documentation is fine, is just a distro thing, gtk-gnutella guys cant do a documentation for each distro. No offense but i think you need to compile more stuff to get used to, compiling thing is not supposed to be easy, thats why repositories exists. The first program i compiled was blender on windows, it took me 3 days, and i even changed the source code, gtk-gnutella is far easy to compile, dont give up.

deb files wont work on your pc magically, you already need to get the dependencies, thats what synaptic do for you, making thing by hands needs you to resolve dependencies.

---

### Post by gabo on 2007-06-18
Well i installed the libxml2-dev. But I still have the following error running ./Configure

Feature Summary (Version 0.96.3):
-------------------------------------------------
GLib version                       : glib-2.x
GUI front-end                      : GTK2
GNU TLS support                    : no
IPv6 support                       : yes
NLS (Native Language Support)      : yes
Fast assertions                    : yes
DBus support (experimental)        : no
SQLite (experimental)              : no
Remote Shell Interface (deprecated): yes
-------------------------------------------------
ERROR: Cannot compile against Gtk+.

Any suggestions?

---

### Post by cbiere on 2007-06-18
If you compile gtk-gnutella yourself, you're better of with a more current SVN snapshot than the release:
[http://gtk-gnutella.sourceforge.net/pub/gtk-gnutella.tar.bz2](http://gtk-gnutella.sourceforge.net/pub/gtk-gnutella.tar.bz2)

Straight-forward instructions for compiling it on Debian-based systems such as Ubuntu are here:
[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian)

This file is also found in the snapshot tarball.

---

### Post by larytet on 2007-12-31
I advice to stick to the 0.96.3 which you get by running
apt-get install gtk-gnutella

succeeded to compile in Ubuntu 7.04 - the Feisty Fawn - released in April 2007  (relatively up to date)

some apt-get should be ran, but after that works
UI looks like Java default gray and white

0.96.4 gives slightly better speeds and faster connects (may be not)

i also edited file ./gtk-gnutella/gwcache in the home directory to include those (added the lines to the ones were there originally)
It probably helps to get connected faster if you add IPs listed on  the web sites below manually to the window Hostcaches

```

http://gwc1c.olden.ch.3557.nyud.net:8090/gwc/
http://gwcrab.sarcastro.com:8001/
http://gwc.ak-electron.org:8080/
http://truly.evil.gtkg.de:443/
http://emak.webcindario.com/g2/indice.php
http://www.student.ru.nl/markjansen/g2/bazooka.php
http://silvers.servehttp.com/g2/bazooka.php
http://g2.sbicomputing.com/g2/bazooka.php
http://g2.wow-toj.be/bazooka.php
http://groovy.syxy.com/g2/
http://jercos.dyndns.org/perlgcache.cgi
http://gwc.downloadmusicinc.com/gcache.cgi
http://andswa.100webspace.net/g2/bazooka.php
http://gwc2.wodi.org/skulls.php
http://www.pione.net/g2/bazooka.php
http://www.k33bz.com/g2/bazooka.php
http://jercos.dyndns.org.nyud.net:8090/~jercos/jgcache
http://anddik.freefronthost.com/baz/bazooka.php
http://mirror.farrugiafamily.com/g2/bazooka.php
http://cache.trillinux.org.nyud.net:8090/g2/bazooka.php
http://cache.trillinux.org/g2/bazooka.php
http://jercos.dyndns.org/~jercos/jgcache
http://midian.jayl.de/g2/bazooka.php
http://tsubasa.ghostwhitecrab.de/
http://fetzig.org:8080/gwc/
http://gwc.monnsta.net/
http://gwc.glucolene.com:8080/
http://gwc.dietpac.com:8080/
http://gwc.nickstallman.net/gcache.asp
http://gwc.nickstallman.net/gcache
http://bazooka1.servehttp.com/g2/bazooka.php
http://cache2.bazookanetworks.com/g2/bazooka.php
http://gwc.nickstallman.net/gcache2.asp
http://gwc.frodoslair.net/skulls/skulls.php

```

---

### Post by cbiere on 2008-01-02
There is really no good reason for sticking to gtk-gnutella 0.96.3. That version is old, expired, dead. If you get connections at all, you'll be drowned in spam and you'll suffer from all the bugs that have been fixed over a year ago.

Regarding GWebCaches, almost all you list have been dead for months if not years. No current Gnutella software uses GWebCaches at all any more. LimeWire does not, FrostWire does not, gtk-gnutella does not.

---

