---
title: "Mplayer Plugin Installation"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-02-03
Hello, I just downloaded the mplayer plugin for firefox from here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) .
I extracted the file to my desktop and now I'm stuck. I have no idea what to do with the contents of the folder. If anyone could give me a step by step installation process I'd appreciate it. Remember, I'm still new at Ubuntu, so try to be descriptive. Thanks!!

---

### Post by benson444 on 2007-02-03
Can't you install this in synaptic? It's called mozilla-mplayer or mplayer-mozilla. You may need to add the extra repositories. Open Synaptic > Settings > Repositories and add universe and multiverse. Reload the package list and search for mplayer.

---

### Post by jingo811 on 2007-02-03
1.)
What is your Ubuntu distro version?

2.)
Install Automatix it makes life easier when installing codecs and stuff!
[http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

3.)
It was a while ago since I did this mplayer solution, but if Automatix doesn't fix your dilemma get back here I have some more quick 'n dirty command lines you can paste into your terminal....(but I don't think you'll need to go through that)

---

### Post by Perfect Storm on 2007-02-03
> **Bofur said:**
> Hello, I just downloaded the mplayer plugin for firefox from here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) .
I extracted the file to my desktop and now I'm stuck. I have no idea what to do with the contents of the folder. If anyone could give me a step by step installation process I'd appreciate it. Remember, I'm still new at Ubuntu, so try to be descriptive. Thanks!!

cd /into/the/extracted/folder
./configure

It might spit out errors if you don't have the needed headers and -dev packages installed. Run ./configure a couple of times and install the right libs it ask for. When it looks good continue:

make
sudo make install

---

### Post by Bofur on 2007-02-03
> **Artificial Intelligence said:**
> cd /into/the/extracted/folder
./configure

It might spit out errors if you don't have the needed headers and -dev packages installed. Run ./configure a couple of times and install the right libs it ask for. When it looks good continue:

make
sudo make install

What does cd mean? Sorry I'm a newbie.

---

### Post by Maestro23 on 2007-02-03
> **Bofur said:**
> What does cd mean? Sorry I'm a newbie.

cd = change directory

---

### Post by taurus on 2007-02-03
> **Bofur said:**
> What does cd mean? Sorry I'm a newbie.

[COLOR="Red"]c[/COLOR]hange [COLOR="Red"]d[/COLOR]irectory.

---

### Post by Bofur on 2007-02-03
So how do you go by cding into the extracted folder?

---

### Post by Perfect Storm on 2007-02-03
Normally the source of an application(s) comes in a tarball (.tar.gz/bz2 etc.) it's like a windows .zip file. Right click on it and choose extract. Then in the terminal;
```
cd <distination>
```

---

### Post by Bofur on 2007-02-03
I tried cd mplayerplug-in in terminal and I get bash: cd: mplayerplug-in: No such file or directory
I've also tried cd desktop/mplayerplug-in and the same error occured. Could you explain what I'm doing wrong?

Thanks for your patience!

---

### Post by taurus on 2007-02-03
What's the output of this command from a terminal?

```
ls -la
```

---

### Post by Bofur on 2007-02-03
I'm sorry, but I dont understand what you mean.. The output it gave me was it could not find the directory if thats what your asking?

---

### Post by taurus on 2007-02-03
I want to know the exact name of that directory so if you would like me to continue helping you, it would be nice if you post the output of something that I've requested.  It makes life much easier than doing a guessing game!

---

### Post by Bofur on 2007-02-03
I'm sorry, I'm still very new at this.
The name of the folder mplayerplug-in and its sitting on my desktop.
I really dont know what else to tell you. :(

---

### Post by Perfect Storm on 2007-02-03
cd ~/Desktop/mplayerplug-in


Linux is case sensitive.

---

### Post by Bofur on 2007-02-03
Okay, I'm getting another problem :)
This is what i did

./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ make
make: *** No targets specified and no makefile found.  Stop.

What does this mean?

---

### Post by Perfect Storm on 2007-02-03
It means you don't have the compiler tool installed. When you want to compile something on Ubuntu the first thing you make sure is that build-essential is installed;

```
sudo aptitude install build-essential
```

It's a meta-package which make sure that you have the basic tools to do compiling.
Also read the first post I made in this thread about compiling. Don't rush into "make" before you read the ./configure output to make sure that evrything is okay.

---

### Post by Bofur on 2007-02-03
Ok got that to work, now its having another problem!

Setting up build-essential (11.3) ...
justin@justin-xt41fi7:~$ cd ~/Desktop/mplayerplug-in
justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
configure: WARNING: mozilla-plugin not found
checking for MOZPLUG... no
configure: WARNING: firefox-plugin not found
checking for MOZPLUG... no
configure: WARNING: seamonkey-plugin not found
checking for MOZPLUG... no
configure: WARNING: xulrunner-plugin not found
configure: error: Unable to find mozilla or firefox development files
justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ make
make: *** No targets specified and no makefile found.  Stop.
justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ 

Any ideas this time? Thanks again for your patience with me! :KS

---

### Post by Perfect Storm on 2007-02-03
```
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
```

This means you need to install the development package of firefox. Everytime there's something missing/error is proplerly because you havn't installed the development package of that program/libs. These -dev packages is needed if you want to compile something (in most cases). So you have to grab firefox dev package;

```
sudo aptitude install firefox-dev
```

---

### Post by Bofur on 2007-02-03
Okay, got that! But yet another problem occured! :( 

justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
configure: WARNING: mozilla-plugin not found
checking for MOZPLUG... yes
checking for GTK... no
configure: WARNING: *** Running in X mode - Limited Features ***
checking for GTK24... no
configure: WARNING: Some GUI Features are disabled
checking for GTHREAD... no
configure: error: Missing gthread package

---

### Post by Perfect Storm on 2007-02-03
> checking for GTK... no
configure: WARNING: *** Running in X mode - Limited Features ***
checking for GTK24... no

You need lib GTK2 -dev it's called libgtk2.0-dev

---

### Post by Bofur on 2007-02-03
Okay I think I got it to work: 
 
```
sudo make install
g++ -c -o plugin.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string -I/usr/include/firefox/nspr   -I/usr/include/firefox -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin.cpp
In file included from Source/plugin.h:55,
                 from Source/plugin.cpp:37:
Source/plugin-setup.h:4:27: error: X11/Intrinsic.h: No such file or directory
Source/plugin-setup.h:5:28: error: X11/StringDefs.h: No such file or directory
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
Source/plugin-setup.h:132: error: ‘Widget’ does not name a type
Source/plugin-setup.h:203: error: variable or field ‘DrawUI’ declared void
Source/plugin-setup.h:203: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘*’ token
Source/plugin-setup.h:203: error: ‘instance’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘char’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: initializer expression list treated as compound expression
Source/plugin-setup.h:206: warning: ‘RedrawCB’ initialized and declared ‘extern’
Source/plugin-setup.h:206: error: variable or field ‘RedrawCB’ declared void
Source/plugin-setup.h:206: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:206: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: initializer expression list treated as compound expression
Source/plugin.h:173: error: ‘Widget’ does not name a type
/usr/include/firefox/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIMemory.h:58: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
Source/plugin.cpp: In constructor ‘nsPluginInstance::nsPluginInstance(NPP_t*)’:
Source/plugin.cpp:207: error: ‘widget’ was not declared in this scope
make: *** [plugin.o] Error 1

```

---

### Post by Perfect Storm on 2007-02-03
Can you please post the whole of your ./configure alot of error output.

---

### Post by Bofur on 2007-02-03
```

justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
configure: WARNING: mozilla-plugin not found
checking for MOZPLUG... yes
checking for GTK... yes
checking for GTK24... yes
checking for GTHREAD... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking X11/Intrinsic.h usability... no
checking X11/Intrinsic.h presence... no
checking for X11/Intrinsic.h... no
checking X11/StringDefs.h usability... no
checking X11/StringDefs.h presence... no
checking for X11/StringDefs.h... no
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strstr... yes
checking for strrchr... yes
checking for snprintf... yes
checking for mkfifo... yes
checking for dup2... yes
checking for gettimeofday... yes
checking for strerror... yes
checking for strtol... yes
checking for mkdir... yes
checking for setlocale... yes
checking for memmem... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... void
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking for DPMSQueryExtension in -lXdpms... no
checking for X11/extensions/dpms.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile
config.status: creating install.sh
config.status: creating uninstall.sh
config.status: creating config.h
config.status: config.h is unchanged
justin@justin-xt41fi7:~/Desktop/mplayerplug-in$ make
g++ -c -o plugin.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/firefox/java -I/usr/include/firefox/plugin -I/usr/include/firefox -I/usr/include/firefox/xpcom -I/usr/include/firefox/string -I/usr/include/firefox/nspr   -I/usr/include/firefox -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin.cpp
In file included from Source/plugin.h:55,
                 from Source/plugin.cpp:37:
Source/plugin-setup.h:4:27: error: X11/Intrinsic.h: No such file or directory
Source/plugin-setup.h:5:28: error: X11/StringDefs.h: No such file or directory
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
Source/plugin-setup.h:132: error: ‘Widget’ does not name a type
Source/plugin-setup.h:203: error: variable or field ‘DrawUI’ declared void
Source/plugin-setup.h:203: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘*’ token
Source/plugin-setup.h:203: error: ‘instance’ was not declared in this scope
Source/plugin-setup.h:203: error: expected primary-expression before ‘char’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: expected primary-expression before ‘int’
Source/plugin-setup.h:204: error: initializer expression list treated as compound expression
Source/plugin-setup.h:206: warning: ‘RedrawCB’ initialized and declared ‘extern’
Source/plugin-setup.h:206: error: variable or field ‘RedrawCB’ declared void
Source/plugin-setup.h:206: error: ‘Widget’ was not declared in this scope
Source/plugin-setup.h:206: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: ‘XtPointer’ was not declared in this scope
Source/plugin-setup.h:207: error: initializer expression list treated as compound expression
Source/plugin.h:173: error: ‘Widget’ does not name a type
/usr/include/firefox/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/usr/include/firefox/nsIMemory.h:58: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
Source/plugin.cpp: In constructor ‘nsPluginInstance::nsPluginInstance(NPP_t*)’:
Source/plugin.cpp:207: error: ‘widget’ was not declared in this scope
make: *** [plugin.o] Error 1
```

---

### Post by Perfect Storm on 2007-02-03
```
sudo make uninstall
make clean
sudo aptitude install libxt-dev xmp-x11 xmp-common xlibs-dev
```

Then try again.

---

### Post by Bofur on 2007-02-03
Ok, it said it was installing for user Justin and then finished. Does that mean thats it?

---

### Post by Perfect Storm on 2007-02-03
Aye, if you have mplayer installed you can now see stuff on the internet (do require w32codecs in most cases).

---

### Post by Bofur on 2007-02-03
Okay, well I can view media just fine, my sound is the problem. On windows, all I had to do was install the flash plugin for firefox/Quicktime to view a site I visit oftenly.. [www.ytmnd.com](www.ytmnd.com)

I just tried viewing one of thier flash movies and it worked fine, but still, I'm getting no sound even with this mplayer plugin that I just installed. Heres an example of a random flash file from there site.

[http://whatyouseeforalleternity.ytmnd.com/](http://whatyouseeforalleternity.ytmnd.com/)

Do I need to install something else to be able to hear sound? Thanks!

---

### Post by Perfect Storm on 2007-02-04
Have you installed Flash 9?

---

### Post by Bofur on 2007-02-04
I download the Adobe Flash 9 file but I dont know how to install it.

---

### Post by Perfect Storm on 2007-02-04
If you downloaded the script (sh) version.
Restract the tarball.

cd <distination>
sudo sh XXXXXXXXXXX.sh

---

### Post by Bofur on 2007-02-04
I got the .tar.gz version.

---

### Post by shareMenaPeace on 2007-02-04
Rightclick it and choose "extract". This unpacks the archive and you can proceed with the above instructions.

---

### Post by OBnascar on 2007-02-04
> **Bofur said:**
> I tried cd mplayerplug-in in terminal and I get bash: cd: mplayerplug-in: No such file or directory
I've also tried cd desktop/mplayerplug-in and the same error occured. Could you explain what I'm doing wrong?

It should be something like this:
cd /home/Bofur/desktop/

---

### Post by Bofur on 2007-02-04
```
justin@justin-xt41fi7:~$ cd ~/Desktop/install_flash_player_9_linux
justin@justin-xt41fi7:~/Desktop/install_flash_player_9_linux$ sudo sh install_flash_player_9_linx.sh
Password:
sh: install_flash_player_9_linx.sh: No such file or directory
justin@justin-xt41fi7:~/Desktop/install_flash_player_9_linux$ 

```

---

### Post by Perfect Storm on 2007-02-04
```
cd ~/Desktop/install_flash_player_9_linux
ls -a
```

---

### Post by jingo811 on 2007-02-13
I think you guys are making life harder than it is.  Why go through all this complicated compiling business when the newbie didn't even know what "cd" meant.  Don't you think that introducing him into the compiling world is a bit early.

As a 1 year old Ubuntu newbie, installing Automatix took care of the majority of my Video, Audio codec needs.  Including those that are experienced through the webbrowser Firefox.
> 
2.)   As I suggested 1 week ago.....
Install Automatix it makes life easier when installing codecs and stuff!
**About this program**: [http://www.getautomatix.com/](http://www.getautomatix.com/)
Install **index** page: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
 
If you really have Ubuntu 6.10 Edgy then this might be for you if you're interested that is...
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)
Click-and-Point at icons and text description that's way more easier I think.  If that doesn't work then I would resort to compiling from source.

---

### Post by Perfect Storm on 2007-02-13
Because it is a good idea to know how linux works and draw some experience, this might lead to that the person can solve and help other people and himself.

---

### Post by jingo811 on 2007-02-13
Your intentions are good but I still think that you are doing it too quickly to the jedi-apprentice.  I don't think a über-Linux-virgin who has never heard of "cd" should go into compiling until they at least got a **"driver license"** 	;-) from these kind of tutorials [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) or even better CLI tutorials that you might have and can recommend to others.

---

