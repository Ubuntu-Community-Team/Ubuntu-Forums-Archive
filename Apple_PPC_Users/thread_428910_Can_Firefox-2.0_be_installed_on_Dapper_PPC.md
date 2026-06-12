---
title: "Can Firefox-2.0 be installed on Dapper PPC?"
date: 2007-04-30
forum: Apple PPC Users
---

### Post by ubuntubrian on 2007-04-30
I have been checking the forums and Mozilla site to try and get Firefox 2.0 installed and running. So far I have downloaded the source code and tried, successfully (at least no errors) to build it. I followed the instructions here:
[http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options)
I got Sunbird up to the latest version using these instructions.

However it seems that Firefox is not so simple as so many other packages depend on it:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
"Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine."

On Bugzilla:
[https://bugs.launchpad.net/dapper-backports/+bug/68158](https://bugs.launchpad.net/dapper-backports/+bug/68158)
They say that it is possible to build a Firefox 2.0 as Firefox2 and run it alongside 1.5 to avoid breaking packages but they don't say how to do this.

It seems possible to build the FF2.0 from source and run it alongside 1.5 but I am not knowledgable enough to do so. I know that the "FirefoxNewVersion" instructions apply to prebuilt debs so that won't work.
I would think the 2.0 version could be built into another directory and renamed but that is beyond me. Can anyone help?

---

### Post by Auria on 2007-04-30
> **ubuntubrian said:**
> I have been checking the forums and Mozilla site to try and get Firefox 2.0 installed and running. So far I have downloaded the source code and tried, successfully (at least no errors) to build it. I followed the instructions here:
[http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options)
I got Sunbird up to the latest version using these instructions.

However it seems that Firefox is not so simple as so many other packages depend on it:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
"Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine."

On Bugzilla:
[https://bugs.launchpad.net/dapper-backports/+bug/68158](https://bugs.launchpad.net/dapper-backports/+bug/68158)
They say that it is possible to build a Firefox 2.0 as Firefox2 and run it alongside 1.5 to avoid breaking packages but they don't say how to do this.

It seems possible to build the FF2.0 from source and run it alongside 1.5 but I am not knowledgable enough to do so. I know that the "FirefoxNewVersion" instructions apply to prebuilt debs so that won't work.
I would think the 2.0 version could be built into another directory and renamed but that is beyond me. Can anyone help?

I've never built FF so these are general instructions

1 - keep the app in place. generally, when building an app, last part is installing it. if the app doesn't require to be installed, you can just leave it there. you'll need to explore a bit the source folders and see where it is, then cd to this dir and do ./firefox
2 - install in a seperate prefix - installing for instance in /usr/local/ when the ubuntu one is in /usr/ is often enough to keep 2 apps seperate. usually when building there is an instruction of what install prefix to use (FF doesnt seem to use autotools so i dont know how though)

---

### Post by ubuntubrian on 2007-04-30
Right, Firefox uses Mozconfig to build and install so it's a bit different. Still not sure how to do it. I think one needs to try the build to see the differences with Mozilla.

---

### Post by Auria on 2007-04-30
> **ubuntubrian said:**
> Right, Firefox uses Mozconfig to build and install so it's a bit different. Still not sure how to do it. I think one needs to try the build to see the differences with Mozilla.

well no matter the build system doesnt affect whether it can be run in place or not. so you can always try that

you'd just need to check how to change install prefix in that.

BTW you'd probably have an easier time installing feisty if you dont need LTS. newer versions have way more recent apps in the repos so its easier to get new stuff

---

### Post by yman on 2007-05-22
> **Auria said:**
> well no matter the build system doesnt affect whether it can be run in place or not. so you can always try that

you'd just need to check how to change install prefix in that.

BTW you'd probably have an easier time installing feisty if you dont need LTS. newer versions have way more recent apps in the repos so its easier to get new stuff

unless you have hardware that for some odd reason works way better in dapper, such as your only means of connecting to the internet (my pc card)

do you think the feisty package would work on dapper?
I tried installing FF2.0.0.3 from source using the default unrecomended configure,  and it gives me the following error message at configure:
> 
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

and when I went ahead and tried to compile anyway ($ make -f client.mk build) it gave me a similar message:
> 
checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** Fix above errors and then restart with               "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/yman/.Trash/mozilla'
make: *** [/home/yman/.Trash/mozilla/Makefile] Error 2

I think I know what it means, but how do I fix it? I tried searching for gtk+-2.0 in synaptic & with the find command and got null. echo $PKG_CONFIG_PATH gives null. $ whereis gtk gives "/etc/gtk" and the contents of that directory are:
> 
gtkrc.az                     gtkrc.ka_GE.georgianacademy
gtkrc.be                     gtkrc.ka_GE.georgianps
gtkrc.bg                     gtkrc.ko
gtkrc.bg_BG.iso88595         gtkrc.lt
gtkrc.cp1251                 gtkrc.lv
gtkrc.cp1255                 gtkrc.mi
gtkrc.cs                     gtkrc.mk
gtkrc.cy                     gtkrc.pl
gtkrc.et                     gtkrc.ro
gtkrc.ga                     gtkrc.ru
gtkrc.he                     gtkrc.ru_RU.iso88595
gtkrc.he_IL.cp1255           gtkrc.sk
gtkrc.he_IL.microsoftcp1255  gtkrc.sl
gtkrc.hr                     gtkrc.sp
gtkrc.hu                     gtkrc.sq
gtkrc.hy                     gtkrc.sr
gtkrc.iso-8859-13            gtkrc.th
gtkrc.iso-8859-14            gtkrc.uk
gtkrc.iso-8859-15            gtkrc.utf-8
gtkrc.iso-8859-2             gtkrc.vi
gtkrc.iso-8859-3             gtkrc.vi_VN.tcvn
gtkrc.iso-8859-5             gtkrc.vi_VN.viscii
gtkrc.iso-8859-7             gtkrc.vi_VN.viscii111
gtkrc.iso-8859-9             gtkrc.yi
gtkrc.ja                     gtkrc.zh_CN
gtkrc.ka                     gtkrc.zh_TW

and from here I'm stuck. without FF2.0.
to me FF2.0 is to FF1.5 like what FF1.5 is to IE6, so I would really like to get set up on this machine ASAP.

UPDATE: yes! I found it! the path is /usr/lib/gtk-2.0
now I need to see if it works.
I had to do $ export PKG_CONFIG_PATH=/usr/lib/gtk-2.0 first.
running ./configure

UPDATE: doesn't work.

---

### Post by Auria on 2007-05-22
Have you installed the gtk-2.0-dev package (or whatever it's called)?
Also it wants gtk+ 2.0 1.3.7 or more, check you have at least this version

PKG_CONFIG_PATH should lead to .am files IIRC

otherwise post whatever error you get, it doesnt work is not of much help

(anyway why dont you just update to edgy of feisty?)

---

### Post by fkdev on 2007-05-22
You obviously aren't very familiar with building stuff from source so here is a rundown of the firefox build:

An explanation of what is happening:
The pkg-config program, called by the configure script (./configure),  is looking for information on the stuff (librairies and headers) needed for building firefox. However, this information and the headers for building are in  various "-dev" packages. For example, in this case libgtk2.0-dev is needed ( along with some other stuff) . So here is how to build your firefox2: 

1. Install firefox build dependencies:
```
 sudo apt-get build-dep firefox 
```
This step install the build dependencies for the package firefox in the repositories. It's an older version, but the dependencies should still match up pretty well.

2. get the  latest source from the mozilla website ( you may have already done this, as yman has, in which case skip this step)
```
 wget "ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/source/*.bz2" -o ~/ 
```

3. unpack the tarball ( if you already have, skip this step too)
```
 cd ~; tar xf *.bz2 
```

4. Make a .mozconfig
```
 cd mozilla; gedit .mozconfig 
```

paste the following to set up firefox (see [http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options) if you want to tweak it):

```

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-firefox
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-xft
ac_add_options --prefix=/opt/firefox
ac_add_options --exec-prefix=/opt/firefox

```

now save and quit gedit.

5. start the build, it's time to compile firefox (this takes a LONG time, so be patient):
```
 make -f client.mk build 
```

Note that this runs configure for us, so the usual ./configure step is not needed

6. If the previous runs without errors, then:
```
 sudo make install 
```
to install

8. Make firefox more easily available under the name firefox2
```
 sudo ln -s /opt/firefox/bin/firefox /usr/local/bin/firefox2 
```

9. Change the menu and toolbar so that firefox2 %u is run instead of firefox %u. I'm sure you can figure this part out pretty easily


Note that these instructions may not be accurate, so if anyone sees anything wrong, please point it out..
EDIT: Ooops, my first instructions were flawed. Sorry, I haven't done this in a while, but I think these should work now....

---

### Post by stmiller on 2007-05-22
You could just download this deb and see if it will install:

[http://packages.ubuntu.com/feisty/web/firefox](http://packages.ubuntu.com/feisty/web/firefox)

PowerPC link is at the very bottom.

---

### Post by ubuntubrian on 2007-05-23
> **fkdev said:**
> You obviously aren't very familiar with building stuff from source so here is a rundown of the firefox build:

An explanation of what is happening:
The pkg-config program, called by the configure script (./configure),  is looking for information on the stuff (librairies and headers) needed for building firefox. However, this information and the headers for building are in  various "-dev" packages. For example, in this case libgtk2.0-dev is needed ( along with some other stuff) . So here is how to build your firefox2: 

1. Install firefox build dependencies:
```
 sudo apt-get build-dep firefox 
```
This step install the build dependencies for the package firefox in the repositories. It's an older version, but the dependencies should still match up pretty well.

2. get the  latest source from the mozilla website ( you may have already done this, as yman has, in which case skip this step)
```
 wget "ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/source/*.bz2" -o ~/ 
```

3. unpack the tarball ( if you already have, skip this step too)
```
 cd ~; tar xf *.bz2 
```

4. Make a .mozconfig
```
 cd mozilla; gedit .mozconfig 
```

paste the following to set up firefox (see [http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options) if you want to tweak it):

```

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-firefox
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-xft

```

now save and quit gedit.

5. start the build, it's time to compile firefox (this takes a LONG time, so be patient):
```
 make -f client.mk build 
```

Note that this runs configure for us, so the usual ./configure step is not needed

6. If the previous runs without errors, then:
```
 make -C obj-firefox/browser/installer installer 
```
to build the installation tarball

7. Install, by unpacking the installation tarball:
```
 cd /opt; sudo tar xf ~/mozilla/obj-firefox/dist/firefox*bz2 
```

8. Make firefox more easily available under the name firefox2
```
 sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox2 
```

9. Change the menu and toolbar so that firefox2 %u is run instead of firefox %u. I'm sure you can figure this part out pretty easily


Note that these instructions may not be accurate, so if anyone sees anything wrong, please point it out..



these are great instructions and I'll try it soon. I finally got Lightning installed to work with Thunderbird and so I'm happy for a little while. the Mozilla site build instructions are somewhat baffling and you've cleared things up considerably!
Thanks:p

---

### Post by ubuntubrian on 2007-05-23
Another question (as Firefox 2.0 is happily building away as per these EXCELLENT instructions)-Will FF2 be able to use the existing mozilla plugins on my system?
Thanks again

---

### Post by ubuntubrian on 2007-05-23
I get this when I try to make the installer:
 make -C obj-firefox/browser/installer installer
make: Entering directory `/home/brianokeefe/mozilla/obj-firefox/browser/installer'
Makefile:69: *** you need a "--enable-static --disable-shared" build to create an installer.  Stop.
make: Leaving directory `/home/brianokeefe/mozilla/obj-firefox/browser/installer'

---

### Post by ubuntubrian on 2007-05-24
> **ubuntubrian said:**
> I get this when I try to make the installer:
 make -C obj-firefox/browser/installer installer
make: Entering directory `/home/brianokeefe/mozilla/obj-firefox/browser/installer'
Makefile:69: *** you need a "--enable-static --disable-shared" build to create an installer.  Stop.
make: Leaving directory `/home/brianokeefe/mozilla/obj-firefox/browser/installer'

I dumped the mozilla folder and rebuilt using the missing items as shown above. the build went fine. When I got to building the installer with:
~/mozilla$ cd /opt; sudo tar xf ~/mozilla/obj-firefox/dist/install/sea/firefox-2.0.0.4.en-US.linux-powerpc.installer.tar.gz
that worked fine too but instead of the /opt/firefox/firefox I ended up with (Firefox2.old isn't anything but an old untarred source offirefox):

brianokeefe@ubuntu:/opt$ ls
Firefox2.old  firefox-installer
brianokeefe@ubuntu:/opt$ cd firefox-installer
brianokeefe@ubuntu:/opt/firefox-installer$ ls
config.ini         firefox-installer-bin  install.ini  watermark.png
firefox-installer  header.png             license.txt  xpi

How do I proceed to install from what i've got here?
Thanks:)

---

### Post by ubuntubrian on 2007-05-24
> **ubuntubrian said:**
> I dumped the mozilla folder and rebuilt using the missing items as shown above. the build went fine. When I got to building the installer with:
~/mozilla$ cd /opt; sudo tar xf ~/mozilla/obj-firefox/dist/install/sea/firefox-2.0.0.4.en-US.linux-powerpc.installer.tar.gz
that worked fine too but instead of the /opt/firefox/firefox I ended up with (Firefox2.old isn't anything but an old untarred source offirefox):

brianokeefe@ubuntu:/opt$ ls
Firefox2.old  firefox-installer
brianokeefe@ubuntu:/opt$ cd firefox-installer
brianokeefe@ubuntu:/opt/firefox-installer$ ls
config.ini         firefox-installer-bin  install.ini  watermark.png
firefox-installer  header.png             license.txt  xpi

How do I proceed to install from what i've got here?
Thanks:)

Also note the different loation of the installer.tar.gz package as opposed to the location in the how-to in this thread:
~/mozilla/obj-firefox/dist/install/sea/firefox-2.0.0.4.en-US.linux-powerpc.installer.tar.gz

---

### Post by ubuntubrian on 2007-05-24
And I just noticed the differences in the 2 versions of the how-to in this thread. One leaves out step 7 and uses "make install". As it doesn't specify installing into /opt I assumed it was the incorrect how-to but perhaps I'm wrong?

---

### Post by yman on 2007-05-24
> **Auria said:**
> Have you installed the gtk-2.0-dev package (or whatever it's called)?
Also it wants gtk+ 2.0 1.3.7 or more, check you have at least this version

PKG_CONFIG_PATH should lead to .am files IIRC

otherwise post whatever error you get, it doesnt work is not of much help

(anyway why dont you just update to edgy of feisty?)

thanks, but in the mean time I installed it using the pre-compiled package available from mozilla.com while following [these instruction]("http://kb.mozillazine.org/Installing_Firefox"). It's working slowly yet smoothly. might have to do with the old hardware, but I'm not so sure. IE7 on windows XP seemed to work at normal speed, and so did FF1.5, opera 9 & Netscape 8. Konqouror on kubuntu also worked at normal speed. so perhaps I should try compiling it with this new advice.

EDIT: FF2 is working at normal speed after all, but the time it takes it to start is dreadful.

I did upgrade to Edgy & Feisty, but came crawling back to Dapper. the reason Is that even though the support for my PC card isn't ideal in Dapper, it's light-years ahead of the newer releases. with Dapper I just run sudo cardmgr to get it working, while with feisty I have to:
1. run sudo cardmgr
2. completely remove pcmciautils
3. install pcmciautils
4. hibernate the computer.
only after following the above steps does it work, and I can't make it permanent because for some odd reason I can only hibernate twice in a row.

PS: by the last "doesn't work" I meant I get the exact same error.
I forgot to mention that I set PKG_CONFIG_PATH to null after doing this.

> **stmiller said:**
> You could just download this deb and see if it will install:

[http://packages.ubuntu.com/feisty/web/firefox](http://packages.ubuntu.com/feisty/web/firefox)

PowerPC link is at the very bottom.

I tried using the Edgy .deb but it gave me a "dependency not satisfiable" over a package that was already installed (forgot the name).

UPDATE: after following the instructions here, it compiled without error (at least thats what it looked like to me).
but then:
> 
sudo checkinstall
Password:

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
true_fopen == 0 for fopen64("/proc/mounts", "r")
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by ubuntubrian on 2007-05-25
It seems to me that the only way to do this is to follow the how-to in this thread but not using "make install". The Mozilla build instructions pretty much say that you need to use their suggestions, as in the how-to. If the Edgy .deb worked then it would probably be easily backported but the dependcy issues are apparently too large to overcome at this time as many apps use the 1.5 version's libraries. Apps like OpenOffice and many others.
As I wrote, I got the build and install to work to a point but don't know how to proceed further.

---

### Post by ubuntubrian on 2007-05-26
I've got FF2.0 running as I write with no glitches! My profile is intact and all my add-ons, bookmarks and extensions but one were automatically loaded. How cool is that!
So use the instructions by Fkdev in this thread but not the ones that are missing step 7! It's not a simple make && make install. You have to use the mozilla build and install parameters as written here by Fkdev:
Originally Posted by fkdev : 



"View Post
You obviously aren't very familiar with building stuff from source so here is a rundown of the firefox build:

An explanation of what is happening:
The pkg-config program, called by the configure script (./configure), is looking for information on the stuff (librairies and headers) needed for building firefox. However, this information and the headers for building are in various "-dev" packages. For example, in this case libgtk2.0-dev is needed ( along with some other stuff) . So here is how to build your firefox2:

1. Install firefox build dependencies:
Code:

 sudo apt-get build-dep firefox

This step install the build dependencies for the package firefox in the repositories. It's an older version, but the dependencies should still match up pretty well.

2. get the latest source from the mozilla website ( you may have already done this, as yman has, in which case skip this step)
Code:

 wget "ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/source/*.bz2" -o ~/

3. unpack the tarball ( if you already have, skip this step too)
Code:

 cd ~; tar xf *.bz2

4. Make a .mozconfig
Code:

 cd mozilla; gedit .mozconfig

paste the following to set up firefox (see [http://developer.mozilla.org/en/docs..._Build_Options](http://developer.mozilla.org/en/docs..._Build_Options) if you want to tweak it):

Code:

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-firefox
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-xft

now save and quit gedit.

5. start the build, it's time to compile firefox (this takes a LONG time, so be patient):
Code:

 make -f client.mk build

Note that this runs configure for us, so the usual ./configure step is not needed

6. If the previous runs without errors, then:
Code:

 make -C obj-firefox/browser/installer installer

to build the installation tarball

7. Install, by unpacking the installation tarball:
Code:

 cd /opt; sudo tar xf ~/mozilla/obj-firefox/dist/firefox*bz2

8. Make firefox more easily available under the name firefox2
Code:

 sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox2

9. Change the menu and toolbar so that firefox2 %u is run instead of firefox %u. I'm sure you can figure this part out pretty easily


Note that these instructions may not be accurate, so if anyone sees anything wrong, please point it out.."


As you'll see in my posts the install tarball ended up in another directory further down but all I did was change the name in the command and it built the tarball fine in /opt. I ended up with a /opt/firefox-installer that I had no idea how to handle as it is a directory full of other files. I ran across the "ultimate" guide here:

[http://ubuntuforums.org/showthread.php?t=330386&page=106](http://ubuntuforums.org/showthread.php?t=330386&page=106)

and found this in the oldest part of the thread:

"This install should not harm your existing Firefox installation. This basically walks you through the official Firefox installer and is mainly for the benefit of people who are worried that it might harm their system or that they might do it incorrectly and overwrite their existing Firefox version.

Let's roll...

Backup your firefox profile, just in case the new version corrupts it (nothing bad happened to my profile).
Code:

$ cd ~/.mozilla
$ tar -cMf firefox.tar firefox/

[HTML][I][B]Now install Firefox 1.1 Alpha 1.
Code:

$cd ~
$ wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/deerpark/alpha1/linux-i686/en-US/deerpark-alpha1.installer.tar.gz
$ tar -zxf deerpark-alpha1.installer.tar.gz[/B][/I][/HTML]
$ sudo firefox-installer/firefox-installer

Installer wizard (custom install):

1. Click Forward
2. Click Accept
3. Select Custom for install type
4. Click Forward
5. Click "Yes" to create the directory
6. Select any components you want to install.
7. Click Forward.
8. Click Install.

Run Firefox 1.1
Code:

$ /usr/local/firefox/firefox

Use the above executable when making a shortcut. Do *not* use the firefox-bin executable."

As I had already installed Firefox-2.0 I ignored the section italicized and just backed up my ~/.mozilla and ran the firefox-installer/firefox-installer section which ran exactly as outline as "Bon Echo" installer. I ran the command and here I am and it works fantastically!!

---

### Post by ubuntubrian on 2007-05-26
As a side note, I downloaded the source tarball directly from Mozilla and did not use the wget command at the beginning of Fkdev's instructions. It probably makes no difference. Also, you obviously need to change the commands as far as the version you download goes. Mine was a .gz tarball not a .bz and the install tarball I created was a powerpc version. Like I said , the directory it ended up being created in was different but that was no problem either.

---

### Post by yman on 2007-05-28
how do I remove the build-dep?
I successfully installed scribus & pidgin thanks to these & other instructions, but now I wan't to get rid of all unnecessary packages because I have little space on my HD - only 6.5 GB total, including the swap partition.

EDIT: PS: FF2.0 is working just fine. I also installed flash-nonfree, & most sun-java packages. FF is a dep of the java plugin, so I had to install it. however, and interestingly, the FF1.5 launcher script launches FF2.0.

---

### Post by milkwood on 2007-12-26
I've tried to install FF2.0.0.11 along with these instructions.And I completed "make -f client.mk build" section.But I failed to make installer showing up Makefile:69: *** you need a "--enable-static --disable-shared" as ubutubrian said.
Therefore I changed moz.config adding "--enable-static --disable-shared".
So I succeeded making installer,but before that I got some error messages,though that might relate with,I couldn't install after all because of an(or some) error.
I think I'm going to try some old versions,but the result is same?
Of cource I'm using Dapper,Gnome and KDE.
Anyone know what should I do?

---

