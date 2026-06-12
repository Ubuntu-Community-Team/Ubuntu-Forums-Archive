---
title: "What is Python, and why did I have to install it?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by emarkay on 2006-10-13
110 Megs of files???  Just to install a printer  - PSC 1350 with HPIJS driver.

And what's POSTFIX?  It asked for info for this?

MRK

PS: here's a screencap...  54 files....


:~$ sudo apt-get install build-essential python2.4-dev python2.4-qt3 li bcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  alien autoconf autotools-dev binutils cpp cpp-4.0 debconf-utils debhelper dpkg-dev g++
  g++-4.0 gcc gcc-4.0 html2text libbeecrypt6 libc6-dev libgcrypt11-dev libgnutls-dev
  libgpg-error-dev liblockfile1 libopencdk8-dev libpopt-dev libqt3-mt librpm4 libsnmp-perl
  libssl-dev libstdc++6-4.0-dev libtasn1-2-dev libwrap0-dev linux-kernel-headers lsb-core
  lsb-cxx lsb-desktop lsb-graphics m4 mailx make ncurses-term pax postfix python2.4-sip4-qt3
  rpm ssl-cert zlib1g-dev
Suggested packages:
  lsb-rpm lintian autoconf2.13 autobook autoconf-archive gnu-standards binutils-doc cpp-doc
  gcc-4.0-locales dh-make debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev flex bison
  gcc-doc libc6-dev-amd64 lib64gcc1 glibc-doc libgcrypt11-doc libgnutls-doc gnutls-bin
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libstdc++6-4.0-doc stl-manual libtool-doc
  g77 fortran77-compiler gcj lsb-qt4 procmail postfix-mysql postfix-pgsql postfix-ldap
  postfix-pcre sasl2-bin python-qt3-doc
Recommended packages:
  libmudflap0-dev libltdl3-dev resolvconf
The following NEW packages will be installed:
  alien autoconf automake1.9 autotools-dev binutils build-essential cpp cpp-4.0
  debconf-utils debhelper dpkg-dev g++ g++-4.0 gcc gcc-4.0 html2text libbeecrypt6 libc6-dev
  libcupsys2-dev libgcrypt11-dev libgnutls-dev libgpg-error-dev libjpeg62-dev liblockfile1
  libopencdk8-dev libpopt-dev libqt3-mt librpm4 libsnmp-perl libsnmp9-dev libssl-dev
  libstdc++6-4.0-dev libtasn1-2-dev libtool libusb-dev libwrap0-dev linux-kernel-headers lsb
  lsb-core lsb-cxx lsb-desktop lsb-graphics m4 mailx make ncurses-term pax postfix
  python2.4-dev python2.4-qt3 python2.4-sip4-qt3 rpm ssl-cert zlib1g-dev
0 upgraded, 54 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB of archives.
After unpacking 110MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [286kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1 [1 407kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls-dev 1.2.9-2ubuntu1.1 [445kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libssl-dev 0.9.8a-7ubuntu0.3 [2023kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main html2text 1.3.2a-3 [95.5kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main debconf-utils 1.4.72ubuntu9 [30.9kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main debhelper 5.0.7ubuntu13 [506kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libbeecrypt6 4.1.2-4 [121kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main postfix 2.2.10-1ubuntu0.1 [923kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main librpm4 4.4.1-5ubuntu2 [933kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main python2.4-dev 2.4.3-0ubuntu6 [1464kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main rpm 4.4.1-5ubuntu2 [597kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main alien 8.64 [104kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main m4 1.4.4-1 [111kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main autoconf 2.59a-7 [381kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main autotools-dev 20050803.1 [58.1kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main automake1.9 1.9.6-1 [515kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libc6-dev 2.3.6-0ubuntu20 [2822kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc 4:4.0.3-1 [5048B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1471kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1386B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main build-essential 11.1 [6826B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libgpg-error-dev 1.1-4 [29.7kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libgcrypt11-dev 1.2.2-1 [237kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main zlib1g-dev 1:1.2.3-6ubuntu4 [405kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libtasn1-2-dev 0.2.17-1ubuntu1 [245kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libpopt-dev 1.7-5 [36.9kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libopencdk8-dev 0.5.7-2 [117kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libcupsys2-dev 1.2.2-0ubuntu0.6.06 [25.7kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libjpeg62-dev 6b-11 [185kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main liblockfile1 1.06.1 [14.1kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libqt3-mt 3:3.3.6-1ubuntu6 [3152kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libsnmp-perl 5.2.1.2-4ubuntu2 [896kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libwrap0-dev 7.6.dbs-8ubuntu1 [32.6kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libsnmp9-dev 5.2.1.2-4ubuntu2 [1268kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libtool 1.5.22-2 [328kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libusb-dev 2:0.1.10a-22ubuntu1 [36.3kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main ssl-cert 1.0.13 [9526B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main mailx 1:8.1.2-0.20050715cvs-1ubuntu1 [153kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main ncurses-term 5.5-1ubuntu3 [277kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main pax 1:1.5-15 [51.3kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main python2.4-sip4-qt3 4.3.2-0ubuntu2 [69.8kB]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main python2.4-qt3 3.15.1-0ubuntu3 [2545kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main lsb-core 3.1-5ubuntu2 [31.1kB]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main lsb-graphics 3.1-5ubuntu2 [11.0kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main lsb-cxx 3.1-5ubuntu2 [11.0kB]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main lsb-desktop 3.1-5ubuntu2 [11.1kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main lsb 3.1-5ubuntu2 [11.0kB]
Fetched 30.5MB in 16m7s (31.5kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package make.
(Reading database ... 72907 files and directories currently installed.)
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package binutils.
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.72ubuntu9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.7ubuntu13_all.deb) ...
Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-4_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.64_all.deb) ...
Selecting previously deselected package m4.
Unpacking m4 (from .../archives/m4_1.4.4-1_i386.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.59a-7_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20050803.1_all.deb) ...
Selecting previously deselected package automake1.9.
********

---

### Post by xXx 0wn3d xXx on 2006-10-13
Python is an interpreter for the Python programming language. Postfix is a mail server. It's most likley not needed but it is most likely a dependency.

---

### Post by harisund on 2006-10-13
Indeed, it is one of Ubuntu's quirks that annoys me, as compared to, say, Gentoo. Why on earth is something like postfix a needed component of ubuntu-desktop? If I try to remove postfix, it removes ubuntu-desktop which eventually breaks my system while upgrading. 

Ubuntu's philosophy kind of reminds me of Apple's. We know what is best for you, so just shut up and use whatever the Ubuntu devs think is the best. If they say postfix is needed, just accept it.

---

### Post by junglepeanut on 2006-10-13
Removing ubuntu-desktop breaks the system? I was under a completely different understanding that it was just a metapackage? Please clarify as to how this causes breakage. Is this something where they add something later to the package so you dont know you need it?? Are you using apt-get or aptitude?

Thanks (If you feel this steals from the thread a pm would be nice or even a post to a sepreate thread/new thread, thanks again.)

---

### Post by emarkay on 2006-10-14
Stealing the thread - no at all - in fact I am a bit intrigued by the "Ubuntu is like Apple" comment above.

I thought all Linux versions played nice with the user and didn't automagically do things that weren't essential, that you could trust the developers to play nice and not install unwanted things (yea, why DOES a printer install need a mail server???????)

Please, go on!  

Need I have to start going back into the "Windows Protective Mode" where I delete all traces of everything after use, scrub the registry weekly, have 3 anti malware programs, don't use most multimedia extensions live on the Internet, haev a hardware and a software firewall, etc. while using UBUNTU???

---

### Post by nereid on 2006-10-14
You just can't release specified packages (you can but then you'll have a miriad of version of the same program), so you just compile everything in your application even if only some people will ever need it. This is the price you have to pay for a binary package system. On the other hand if you are using Gentoo you can specify everything what should be compiled into the application resulting in stream lined versions tailored to your needs at the price of the compile time and the hassle to compile packages.

---

### Post by PriceChild on 2006-10-14
ubuntu-desktop is a meta package.

Its removal will only cause breakage if it is not installed in a dev version or during an upgrade from one version to the next - e.g. 6.06 --> 6.10

When you install a package using apt, all dependencise are handled for you. If it didn't, we would isntead see hundreds of comments asking why not all features of programs work.

Many packages have "reccomended" dependencies which aren't always needed.

---

### Post by CatKiller on 2006-10-14
The reason you're installing 110 Megs of stuff is because you've decided to install 110 Megs of stuff. From what I can see, you're installing a Python development environment. Presumably so that you can compile someone's program. It's hardly Ubuntu's fault if it does exactly what you tell it to, now, is it?

---

### Post by K.Mandla on 2006-10-14
I'm likewise a little confused. If I read it right, your original command was
 
```
sudo apt-get install build-essential python2.4-dev python2.4-qt3 li bcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev
```
It looks like you're telling it to install the python development packages. Why not just 

```
sudo aptitude remove python2.4-dev python2.4-qt3
```
And so forth.

And without oversimplifying the issue, is it not possible to use the gnome-cups-manager interface to install your printer?

Sorry if I've missed the mark here. :(

---

### Post by emarkay on 2006-10-14
Folks, the #%*&(*&^@$#(* program installed all this stuff automatically!  

[http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/)

"I vas only following orders!"  (I did what it said!)

---

### Post by K.Mandla on 2006-10-14
Understandable. Again, in that case, if the HP Inkjet project used Python to build their utility, you'll probably need Python to run it. So we're kind of saying the same thing ... yes, if you want to run their utility, it's going to take 110Mb of extra packages to work. :-? Sorry.

Just out of curiosity, have you tried to configure your printer with the gnome-cups-manager? What model of printer is it? (Edit: Never mind. I reread the OP.)

---

### Post by Delkster on 2006-10-14
> **harisund said:**
> If I try to remove postfix, it removes ubuntu-desktop which eventually breaks my system while upgrading.
I don't generally have ubuntu-desktop installed but I install it when it's time to upgrade the distribution just to make the upgrade smoother. It doesn't happen so often that I couldn't install the package for the duration of the upgrade and remove whatever I want after that.

> Ubuntu's philosophy kind of reminds me of Apple's. We know what is best for you, so just shut up and use whatever the Ubuntu devs think is the best. If they say postfix is needed, just accept it.
Most people who aren't computer experts don't actually know enough to understand whether they want certain components installed, so it's a safe bet to have them included if you also want non-experts to be able to install and use the system.

If you're an expert, you know how to get rid of the stuff you don't need anyway.

---

### Post by Delkster on 2006-10-14
> **emarkay said:**
> Folks, the #%*&(*&^@$#(* program installed all this stuff automatically!  

[http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/)

Are you sure that the HP InkJet components you need aren't already included in the Ubuntu? Is there a specific need to install something from that website by hand? As others have asked, have you tried just adding your printer through **System > Administration > Printing**?

---

### Post by K.Mandla on 2006-10-14
It looks like the PSC 1350 might work with drivers from a similar model. 

[http://www.ubuntuforums.org/showpost.php?p=586984&postcount=3](http://www.ubuntuforums.org/showpost.php?p=586984&postcount=3)

You'll have to try it out to see. I'm using a Lexmark here. :p

---

### Post by emarkay on 2006-10-15
Thanks for the comments - I am learning by doing - at such a rate my brain hurts at times :)

Honestly, I haven't had time to delve into all the nuances of the printer functions.  Like I said the repository version is 0.9.7 and the sourceforge driver is 1.6.9.  I wanted to get the "official" HP driver and then I'll take it from there.  

I sort of overreacted, because now I have learned about "dependencies" and all that this morning.

It's like going from the "C Prompt" to "File Manager" all over again!  :)

Thanks again!

---

### Post by Delkster on 2006-10-15
> **emarkay said:**
> Like I said the repository version is 0.9.7 and the sourceforge driver is 1.6.9.  I wanted to get the "official" HP driver and then I'll take it from there.

The difference in version numbers seems high but if you look at the release history in "Latest News" on the SF website, the version number once received a large bump, and there are even 0.9.x versions from last spring, so they aren't overly old.

I understand your aim for the most recent drivers possible (I know that from the time I mainly used Windows), but if it works (i.e. your printer isn't too new to be supported by the older version), there probably isn't a great difference since the drivers have been working fine for a while.

Ubuntu just packages the official driver (although possibly with its own patches) so it's pretty much the same except that the version specifically packaged for Ubuntu is at least quite certain to integrate well with the rest of the system.

---

