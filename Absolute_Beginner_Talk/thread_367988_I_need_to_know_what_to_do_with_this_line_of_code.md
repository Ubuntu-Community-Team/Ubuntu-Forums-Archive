---
title: "I need to know what to do with this line of code"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Tag_yer_dead on 2007-02-22
Hi guys
Im going through a tutorial on how to install packages in the command line, and need to know what files i need to get from Synaptic Package Manager.
I am in my correct folder. and typed "./configure" and got


gaim-xfire-0.6.0
corey@corey-desktop:~/Desktop$ cd gaim-xfire-0.6.0
corey@corey-desktop:~/Desktop/gaim-xfire-0.6.0$ ./configure
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
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.


What files do i need to get from Synaptic to make this install work, please be specific including their file extensions, i want to be able to do this again without questions.

---

### Post by Maestro23 on 2007-02-22
Need build-essential for starters.

> sudo aptitude update 

sudo aptitude install build-essential


Good link to bookmark: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by teaker1s on 2007-02-22
> **Tag_yer_dead said:**
> Hi guys
Im going through a tutorial on how to install packages in the command line, and need to know what files i need to get from Synaptic Package Manager.
I am in my correct folder. and typed "./configure" and got


gaim-xfire-0.6.0
corey@corey-desktop:~/Desktop$ cd gaim-xfire-0.6.0
corey@corey-desktop:~/Desktop/gaim-xfire-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working [COLOR="Red"]aclocal-1.4.[/COLOR].. missing
checking for working [COLOR="Red"]autoconf[/COLOR]... missing
checking for working [COLOR="Red"]automake-1.4[/COLOR]... missing
checking for working [COLOR="Red"]autoheader[/COLOR]... missing
checking for working [COLOR="Red"]makeinfo[/COLOR]... missing
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
configure: error: pkg-config could not locate either [COLOR="Red"]libssl.pc[/COLOR] or [COLOR="Red"]openssl.pc[/COLOR]
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.


What files do i need to get from Synaptic to make this install work, please be specific including their file extensions, i want to be able to do this again without questions.

need installed build-essential and the  red bits

---

### Post by Tenicus on 2007-02-22
All you had to do was go into synaptic and search for what it gave you.
Anyways, this should work: libssl-dev.  I didnt see an openssl-dev package

---

### Post by Tag_yer_dead on 2007-02-22
Thanks guys, learned a lot from that, but still ahve a few problems.... First after installing all the things that were missing i get this......

checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing

When i try to install using "sudo aptitude install makeinfo" i get

Couldn't find any package matching "makeinfo".  However, the following
packages contain "makeinfo" in their description:
texi2html 


Finally, i have one more question lol
When checking ./configure i get this

configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.

i used "sudo aptitude install libssl.pc" and got success, and "sudo aptitude libssl.pc" and had success, but that bottom part still comes up.
I also tried "sudo apt....... openssl" and "sudo apt....... libssl"

Please help guys im so close to understanding thing lol

---

### Post by Bloch on 2007-02-22
> Im going through a tutorial on how to install packages in the command line,

In fact what you are doing is compiling aprogram from source code. This is specialist stuff - you can spend your whole life as a computer techie without compiling.

Good luck to you, but do remember you're jumping way out of the beginner's level. All software that has been tested and is well-known is available in binary form, and usually in the repositories, (i.e synaptic)

I think it's important to point this out in the beginner's section because it often happens that when you do a search for a particular program you get to the source code page with instructions on how to compile it. 
This is great if you want to use the 2-day-old version of software!

---

### Post by Tag_yer_dead on 2007-02-22
well none the less, ne ideas?

OR

does ne one have ne simpler ways to get Xfire on to Gaim
(Currently im trying a thing called GFire which acts as an extention for Gaim)

---

### Post by aysiu on 2007-02-22
You don't want to try something like this? ```
wget -c http://superb-east.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb
sudo dpkg -i gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb
```

---

### Post by Tag_yer_dead on 2007-02-23
corey@corey-desktop:~/Desktop/Installers$ ./gaim-xfire-0.6.0/configure
cat: ./VERSION: No such file or directory
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
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



I still cant find the makeinfo, and then how do i use PKG_CONFIG_Path?

---

### Post by Tag_yer_dead on 2007-02-23
bump.... sry

---

### Post by aysiu on 2007-02-23
See post #8.

---

### Post by Tag_yer_dead on 2007-02-23
ya sorry i forgot to acknowledge i tried that to, and doesnt work....
I get

(Reading database ... 116712 files and directories currently installed.)
Preparing to replace gaim-xfire 0.6.0-gaim1.5-dapper1 (using gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb) ...
Unpacking replacement gaim-xfire ...
Setting up gaim-xfire (0.6.0-gaim1.5-dapper1) ...
corey@corey-desktop:~$ wget -c [http://superb-east.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb](http://superb-east.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb)
--23:23:09--  [http://superb-east.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb](http://superb-east.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb)
           => `gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

  [COLOR="Red"]  The file is already fully retrieved; nothing to do.[/COLOR]

corey@corey-desktop:~$ sudo dpkg -i gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb
(Reading database ... 116712 files and directories currently installed.)
Preparing to replace gaim-xfire 0.6.0-gaim1.5-dapper1 (using gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb) ...
Unpacking replacement gaim-xfire ...
Setting up gaim-xfire (0.6.0-gaim1.5-dapper1) ...

It says its successful but still no xfire in the add accounts section.
Is there ne thing i need to do after i installed it?

---

### Post by msak007 on 2007-02-23
Whenever you're compiling an app from source and it fails on a dependency, chances are it's looking for the dev files. In this case, it's saying Gaim is not available because you most likely installed it from the repositories, and don't have any of the dev files installed. If you really want to pursue installing from source, you can try the following:

```
 sudo aptitude install gaim-dev
```Then try to compile again. Or you could just do what aysiu has already said (twice) - post #8 has instructions for installing a pre-compiled .deb so you don't have to mess with installing all the -dev packages and compiling from source.

P.S. In the future if you're ever missing a file you can't find (in your case the *ssl.pc files), you can try the following command and it'll tell you which package(s) contains the file(s) you're looking for:

```
sudo apt-file search <filename>
```In this case, 

```
sudo apt-file search libssl.pc
``` returned the result

```
**libssl-dev**: usr/lib/pkgconfig/libssl.pc
```The first part of the output (the part I've bolded) tells you which package it's in.

EDIT: Sorry I see that since I started replying you've tried the .deb that aysiu linked to. Are you using Gaim 1.5 or the 2.0 beta?

---

### Post by aysiu on 2007-02-23
> **Tag_yer_dead said:**
> ```
corey@corey-desktop:~$ sudo dpkg -i gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb
(Reading database ... 116712 files and directories currently installed.)
Preparing to replace gaim-xfire 0.6.0-gaim1.5-dapper1 (using gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb) ...
Unpacking replacement gaim-xfire ...
Setting up gaim-xfire (0.6.0-gaim1.5-dapper1) ...
``` It says its successful but still no xfire in the add accounts section.
Is there ne thing i need to do after i installed it? I agree. It looks successful. Now the key is to find out how to use it or where it is. Honestly can't help you there. I don't even know *what* xfire is!

Consider it installed, though. You just have to figure out now how to use it...

---

### Post by aidanr on 2007-02-24
i installed the deb and fired up gaim 2.0 beta3 in debug mode and this error came up

```
plugins: probing /usr/lib/gaim/libxfire.so
plugins: /usr/lib/gaim/libxfire.so is unloadable: undefined symbol: gaim_url_fetch
plugins: /usr/lib/gaim/libxfire.so is unloadable: ABI version mismatch 1.5.x (need 2.0.x)
```

it should show up in tools -> plugins, just have to find the right version

edit:// [http://ovh.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-g2.0b3-r2-ubuntu1_i386.deb](http://ovh.dl.sourceforge.net/sourceforge/gfire/gaim-xfire_0.6.0-g2.0b3-r2-ubuntu1_i386.deb) worked for me, and i was wrong it shows up in accounts -> add/edit

---

### Post by msak007 on 2007-02-24
> **aidanr said:**
> i installed the deb and fired up gaim 2.0 beta3 in debug mode and this error came up

```
plugins: probing /usr/lib/gaim/libxfire.so
plugins: /usr/lib/gaim/libxfire.so is unloadable: undefined symbol: gaim_url_fetch
plugins: /usr/lib/gaim/libxfire.so is unloadable: ABI version mismatch 1.5.x (need 2.0.x)
```it should show up in tools -> plugins, just have to find the right version
That's why I asked if he's using 1.5 of 2.0 beta - I would assume the plugins are different for the new version, and if he's using any version of 2.0 the 1.5 plugin won't work.

**Tag_yer_dead** : Can you confirm which version of Gaim you're using (1.5 or 2.0 beta x), and if you are using 2.0 run it from the terminal and post any output relating to xfire.

---

### Post by Tag_yer_dead on 2007-02-24
i am using 1.5
and still no luck with getting it to work, and i cant figure out wy

---

### Post by aidanr on 2007-02-24
run this command
```
gaim -d|grep plugin>~/gaim.log
```
then quit gaim and attach the file gaim.log in your home folder to your next post

---

### Post by Tag_yer_dead on 2007-02-24
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgaimperl.so
plugins: /usr/lib/gaim/libgaimperl.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: /usr/lib/gaim/tcl.so is unloadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/timestamp_format.so
[COLOR="Red"]plugins: probing /usr/lib/gaim/libxfire.so[/COLOR]
plugins: /usr/lib/gaim/libxfire.so is unloadable: undefined symbol: gaim_url_fetch
plugins: /usr/lib/gaim/libxfire.so is unloadable: ABI version mismatch 1.5.x (need 2.0.x)
plugins: Loading saved plugin /usr/lib/gaim/statenotify.so
plugins: Loading saved plugin /usr/lib/gaim/ssl-gnutls.so
plugins: Loading saved plugin /usr/lib/gaim/gaimrc.so
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Loading saved plugin /usr/lib/gaim/psychic.so
plugins: Loading saved plugin /usr/lib/gaim/ssl.so
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
docklet: plugin loaded
main: Unloading all plugins
plugins: Unloading plugin System Tray Icon
docklet: plugin unloaded
plugins: Unloading plugin Gaim GTK+ Theme Control
plugins: Unloading plugin Gadu-Gadu
plugins: Unloading plugin IRC
plugins: Unloading plugin Jabber
plugins: Unloading plugin MSN
plugins: Unloading plugin GroupWise
plugins: Unloading plugin AIM/ICQ
plugins: Unloading plugin Sametime
plugins: Unloading plugin SIMPLE
plugins: Unloading plugin Yahoo
plugins: Unloading plugin Message Notification
plugins: Unloading plugin Perl Plugin Loader
plugins: Unloading plugin Psychic Mode
plugins: Unloading plugin GNUTLS
plugins: Unloading plugin SSL
plugins: Unloading plugin Buddy State Notification



Xfire does show up in there
Ne ideas now?

---

### Post by Tag_yer_dead on 2007-02-24
ne one have ne ideas?

---

### Post by aidanr on 2007-02-24
well, thats the exact same error i got, did you try installing the deb i linked?

---

### Post by Adramelech on 2007-02-24
To be honest i recall having the same problem when installing from synaptic, i use Game 3.1 beta and i compiled Gfire from source and it works fine here now.

---

### Post by Tag_yer_dead on 2007-02-24
how do you do that?

---

### Post by Adramelech on 2007-02-25
Following the readme instructions, try getting help on IRC i think is a better option to you to understand the compilation process and get faster answers.

---

