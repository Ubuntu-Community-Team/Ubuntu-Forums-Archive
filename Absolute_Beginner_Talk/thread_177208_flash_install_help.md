---
title: "flash install help"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by avidsensei on 2006-05-15
ok so i was doing the wiki install or whatnot for flash useing a 32bit firefox
and it is not working too well so heres what i did how do i get it to work?


kyle@fast64:~$ sudo apt-get install ia32-libs ia32-libs-gtk linux32
Password:
Reading package lists... Done
Building dependency tree... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
linux32 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@fast64:~$ cd ~/Desktop/firefox
kyle@fast64:~/Desktop/firefox$ mkdir /usr/local/firefox32
mkdir: cannot create directory `/usr/local/firefox32': File exists
kyle@fast64:~/Desktop/firefox$ cp -r -p ./* /usr/local/firefox32/
kyle@fast64:~/Desktop/firefox$ sudo gedit /etc/pango32/pangorc &
[1] 9911
kyle@fast64:~/Desktop/firefox$ sudo gedit /etc/pango32/pangorc &
[2] 9935
[1]   Done                    sudo gedit /etc/pango32/pangorc
kyle@fast64:~/Desktop/firefox$ sudo gedit /usr/local/bin/firefox32 &
[3] 9953
[2]   Done                    sudo gedit /etc/pango32/pangorc
kyle@fast64:~/Desktop/firefox$ sudo bash
root@fast64:~/Desktop/firefox# apt-get install gsfonts
Reading package lists... Done
Building dependency tree... Done
gsfonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@fast64:~/Desktop/firefox# apt-get install gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
gsfonts-x11 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@fast64:~/Desktop/firefox# cd ~/Desktop/
root@fast64:~/Desktop# linux32 ./install_flash_player_7_linux/flashplayer-installer

Copyright(C) 2002-2003 Macromedia, Inc.  All rights reserved.

Macromedia Flash Player 7 for Linux

Macromedia Flash Player 7 will be installed on this machine.

You are running the Macromedia Flash Player installer as the "root" user.
Macromedia Flash Player 7 will be installed system-wide.

Support is available at [http://www.macromedia.com/support/flashplayer/](http://www.macromedia.com/support/flashplayer/)

To install Macromedia Flash Player 7 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11.

Press ENTER to continue...



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/local/firefox32/

WARNING: An older version of the Macromedia Flash Player has been detected in
         /usr/local/firefox32//plugins.
         The installer will overwrite this existing binary.



----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Browser installation directory = /usr/local/firefox32/

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): y

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/local/firefox32/

WARNING: An older version of the Macromedia Flash Player has been detected in
         /usr/local/firefox32//plugins.
         The installer will overwrite this existing binary.



----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Browser installation directory = /usr/local/firefox32/

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Macromedia Flash Player installation is complete.

root@fast64:~/Desktop# firefox32 &
[1] 10083
root@fast64:~/Desktop# Cannot execute /path/to/firefox/firefox: No such file or directory
/usr/local/bin/firefox32: line 5: [WWW]: command not found

[1]+  Exit 127                firefox32
root@fast64:~/Desktop# sudo bash
root@fast64:~/Desktop# sudo -l
User kyle may run the following commands on this host:
    (ALL) ALL
root@fast64:~/Desktop#

---

### Post by aysiu on 2006-05-15
[QUOTE=avidsensei]ok so i was doing the wiki install or whatnot for flash useing a 32bit firefox
and it is not working too well so heres what i did how do i get it to work?[/QUOTE] Wait.. what is all that stuff you just did? [The Wiki instructions](https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b) just say to [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then paste this command into a terminal: ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by avidsensei on 2006-05-15
FirefoxAMD64FlashJava
Firefox 1.5, Flash and Java in amd64 Ubuntu Breezy installations

{i} This is currently working in Dapper 6.06.6 rather well.
You can run Flash and Java plugins in AMD64 bit computers with Firefox, just follow these easy steps :

What we are going to do is install 'Firefox 1.5 32 bit version', using linux32 execution command. (Without the complicated 'chroot' method)

With this method you can't use the original 'Firefox' from Ubuntu and this new installation at the same time, but it doesn't matter because you won't use the default navigator anymore ;) , for this reason is a good idea print this manual and shut down Firefox browser.

1 - Install suport for 32 bit applications :

    *

      sudo apt-get install ia32-libs ia32-libs-gtk linux32

2 - Download firefox 32 bit version from [www.getfirefox.com](www.getfirefox.com)

    *

      [WWW] [http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US)

      (Another kind of installation is in FirefoxNewVersion which however differs in some details (installs into /opt; replaces regular /usr/bin/firefox with a new command), but I never tested :S )

3 - Untar the downloaded file like you allways do in Ubuntu, and go inside the directory :

    *

      cd ~/Desktop/firefox

      (or go where the uncompressed file is)

4 - Create a folder for the 32 bit firefox installation, and copy firefox there :

    *

      mkdir /usr/local/firefox32

      cp -r -p ./* /usr/local/firefox32/

5 - Create the execution files for 32 bit firefox :

    *

      sudo gedit /etc/pango32/pangorc &

    *

      Next add this text to the file :
          o

            [Pango]

            ModuleFiles=/etc/pango32/pango.modules

            [PangoX]

            AliasFiles=/etc/pango/pangox.aliases

      Then create another file :
          o

            sudo gedit /usr/local/bin/firefox32 &

      Next add this text to the file :
          o

            
      [WWW] [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

9 - Install flash player :

    *

      sudo bash

      apt-get install gsfonts

      apt-get install gsfonts-x11

      cd ~/Desktop/

      linux32 ./install_flash_player_7_linux/flashplayer-installer

      (When the installer asks you for the 'navigator path', write : /usr/local/firefox32/)

10 - Check if your new Firefox is working with flash, restart the browser and visit : [WWW] [http://www.macromedia.com](http://www.macromedia.com)

    *

      firefox32 &

11 - To install Java player to run applets, go to [WWW] [http://www.java.com](http://www.java.com), and download the linux self stracting file for 32 bit linux computers (I was surprised to see than this file works in amd64 bits Breezy installation) :

    *

      [WWW] [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

12 - To install java :

    *

      sudo bash

      chmod 777 ./jre-1_5_0_06-linux-i586.bin

      (this file name will depend on the java version you download)

      ./jre-1_5_0_06-linux-i586.bin

      (it will ask you some questions)

      mkdir /usr/local/java32

      cp -r -p ./jre1.5.0_06/* /usr/local/java32

      cd /usr/local/firefox32/plugins/

      ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./

13 - Restart firefox32 and check if java is working :

    *

      firefox32 &

14 - Visit : [WWW] [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

15 - Add an icon at the top panel to start this 'cool' browser :

    *

      Click with the right button at the top panel

      Choose : Add to panel

      Choose : Custom application launcher, and press 'Add' button
          o

            Name : firefox32

            Generic name : Firefox 1.5 32 bits

            Comment : Firefox with 'Flash' and 'Java'

            Command : firefox32

            Type : Application

            Icon : /usr/share/pixmaps/mozilla-firefox.png

16 - Enjoy the net !

IMPORTANT NOTE:

    *

      PhilOSparta said in 'Ubuntu forums' that sound was not working properly for him. He solved the problem using the next line (Ubuntu Dapper with gstreamer0.10 will have this issue solved) :

      sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
#!/bin/sh

            export GTK_PATH=/usr/lib32/gtk-2.0

            export PANGO_RC_FILE=/etc/pango32/pangorc

            linux32 /usr/local/firefox32/firefox $@

6 - Make it executable :

    *

      sudo chmod +x /usr/local/bin/firefox32

7 - Check if your new 32 bit firefox is working :

    *

      firefox32 &

      (it says warnings but doesn't matter)

8 - To install flash, download linux 32 bit flash player from macromedia and untar it :

    *

Thanks for your attention, kisses

Albert Palacios
Adding RealPlayer Support

Thanks to the above help, I was also able to get my dearly loved BBC news via the following technique:
Download RealPlayer10GOLD.bin from Real

[WWW] RealPlayer10GOLD.bin
Make the RealPlayer10GOLD.bin binary executable

cd ~/Desktop 
chmod a+x RealPlayer10GOLD.bin

Install using linux32

sudo linux32 ./RealPlayer10GOLD.bin 

Follow the instructions as indicated. Install to /usr/local/realplayer32/ for consistency sake.
Copy relevant plugins to your Firefox 32bit directory

cd /usr/local/realplayer32/mozilla/ 
sudo cp * /usr/local/firefox32/plugins

Test

Shutdown all instances of Firefox and restart your firefox32 as per above. Go to [www.bbc.com](www.bbc.com) and try the listen live radio portions to test.

Good luck.

This tutorial has been modified, these are some notes from the tutorial before last changes (which hopefully solved these problems)

    *

      If you are having problems with segmentation faults when trying to use the browser's or email client's "Open" or "Execute" methods for opening data files or attachments in helper applications (such as 'evince' for PDFs), then try this alternative method:

Change the files 'firefox32' and 'thunderbird32' to read

#!/bin/sh

export GTK_PATH=/usr/lib32/gtk-2.0

export LD_PRELOAD=/usr/lib32/libpangohack.so.0

linux32 /usr/local/<firefox/thunderbird>32/<firefox/thunderbird> $@

    *

      Note that this method is untested AFAIK - please post any potential issues with it. Many thanks to 'lychee' from the forums.

DrBob: just 2 comments

    *

      sound is an issue under KDE (Kubuntu) as well. The arts daemon (if running) must be suspended in order for Flash to be able to emit sound.
    *

      with the above procedure, the fonts used by firefox32 don't match those in the ubuntu-packaged version. I don't know how to fix this (those that appear in firefox32 are oversized for me, YMMV). NB. I'm talking about the fonts used in the GUI, not those used in rendering webpages (but the latter don't quite match either).

Discuss this page at [WWW] [http://ubuntuforums.org/showthread.php?p=626612](http://ubuntuforums.org/showthread.php?p=626612)

CategoryDocumentation CategoryCleanup

last edited 2006-05-09 02:01:19 by TroySobotka

---

### Post by avidsensei on 2006-05-15
that the directions, havent gotten to the java part


sorry forgot to mention that im useing x86_64

---

### Post by avidsensei on 2006-05-15
root@fast64:~/Desktop# sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
root@fast64:~/Desktop#

---

### Post by avidsensei on 2006-05-15
that dident work

---

### Post by aysiu on 2006-05-15
Are you using x86 or AMD64? I'm confused here.

If you're using a 64-bit processor, Flash won't be so easy: > Flash for AMD64 and PPC

    *

      "For those of us with 64-bit processors (or Mac) there is no non-free flash implementation available because the manufacturer does not support them. However, there are two free implementations. One is gplflash and the other is swfdec. There is also gplflash2 in development that aims to be the proper free, open source replacement for all the platforms. While you can install them using apt-get, they tend not to work very well and are unstable, so that option is not great. Better to install one of them (I recommend gplflash) manually." If you are determined, another option is to install a i386 ubuntu in a DebootstrapChroot and launch your browser with flash plugin from there. [Here are the Wiki instructions for GPLFlash](https://wiki.ubuntu.com/RestrictedFormats#head-f4b5a0e592cf89fac0bb7f5388c8e1733413af21), but you may not have much luck with that.

As for *flashplugin-nonfree*, that's available for x86 *only*.

---

### Post by fornix on 2006-05-15
You need to enable all the sources
fornix@fusion:~$ sudo vim /etc/apt/sources.list
enable all the sources by removing # from appropriate lines (starting with deb...).
fornix@fusion:~$ sudo apt-get update

now try doing. it should find the package

---

### Post by catlett on 2006-05-15
Who is giving you those directions??? It is very simple. Go here to download flash. [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Then follow the instructions.
> Installation Instructions

1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).
If thes are a little complicated this is a breakdown. Download this file to your Desktop. Drag it into your home folder. Right click on the tar file and choose "extract here".
Go to the terminal```
 cd  /install_flash_player_7-linux
```
Then enter ```
 ./flashplayer-installer 
```
Follow the prompts in the terminal. If it says enter path (/usr/lib/mozilla)...What is in parentheses is what the installer thinks is the default location. Just enter what is in the parentheses /usr/lib/mozilla.
This is how I did it and I don't see why you can't. I don't know what all that stuff is you're doing? Maybe I'm missing something?


P.S. I am missing something Aysiu just pointed out you are running AMD64. Disregard my post. I'm leaving it up in case someone with regular 32 bit system stumbles upon it. Good luck.

---

### Post by Sef on 2006-05-15
You can also get it by reading this wiki:

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by avidsensei on 2006-05-16
i dont think you understand, it is a 64bit processor. and running 64bit ubuntu... and now my browser is getting really messed up

---

### Post by avidsensei on 2006-05-16
how do you uninstall that gplflash... i did the apt get by mistake

---

### Post by aysiu on 2006-05-16
[QUOTE=avidsensei]i dont think you understand, it is a 64bit processor. and running 64bit ubuntu... and now my browser is getting really messed up[/QUOTE] This part of your first post probably confused people--I know it confused me: > ok so i was doing the wiki install or whatnot for flash useing a 32bit firefox
and it is not working too well so heres what i did how do i get it to work?

---

### Post by catlett on 2006-05-16
Are you following this how to? [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)

---

### Post by avidsensei on 2006-05-16
kyle@fast64:~$ cd  /install_flash_player_7-linux
bash: cd: /install_flash_player_7-linux: No such file or directory
kyle@fast64:~$  ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
kyle@fast64:~$ cd /home/install_flash_player_7-linux
bash: cd: /home/install_flash_player_7-linux: No such file or directory
kyle@fast64:~$ cd /home/kyle/flash
kyle@fast64:~/flash$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

kyle@fast64:~/flash$

---

### Post by avidsensei on 2006-05-16
yeah sorry i mean i was trying to install a 32bit version of firefox on my 64 machine so i could use flash properly

---

### Post by avidsensei on 2006-05-16
ok i got it uninstalled... should be good to start from scratch... and suggestions?

---

### Post by avidsensei on 2006-05-16
ok so i tried aysiu's suggestion and heres what i got


dpkg: error processing /home/kyle/gplflash-0.4.13/gplflash-0.4.13_0.4.13-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 /home/kyle/gplflash-0.4.13/gplflash-0.4.13_0.4.13-1_x86_64.deb

---

### Post by avidsensei on 2006-05-16
ok so i installed it correctly this time but i still dont have flash in firefox...



kyle@fast64:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
kyle@fast64:~$ sudo apt-get install libx11-dev xlibs-dev libmad0-dev libjpeg-dev checkinstall build-essential
Reading package lists... Done
Building dependency tree... Done
libx11-dev is already the newest version.
xlibs-dev is already the newest version.
libmad0-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
checkinstall is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@fast64:~$  wget -c [http://heanet.dl.sourceforge.net/sourceforge/gplflash/gplflash-0.4.13.tar.bz2](http://heanet.dl.sourceforge.net/sourceforge/gplflash/gplflash-0.4.13.tar.bz2)
--23:47:55--  [http://heanet.dl.sourceforge.net/sourceforge/gplflash/gplflash-0.4.13.tar.bz2](http://heanet.dl.sourceforge.net/sourceforge/gplflash/gplflash-0.4.13.tar.bz2)
           => `gplflash-0.4.13.tar.bz2'
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

kyle@fast64:~$   tar xvjf gplflash-0.4.13.tar.bz2
gplflash-0.4.13/
gplflash-0.4.13/ChangeLog
gplflash-0.4.13/AUTHORS
gplflash-0.4.13/COPYING
gplflash-0.4.13/Makefile.am
gplflash-0.4.13/INSTALL
gplflash-0.4.13/autogen.sh
gplflash-0.4.13/NEWS
gplflash-0.4.13/README
gplflash-0.4.13/TODO
gplflash-0.4.13/configure.in
gplflash-0.4.13/compile
gplflash-0.4.13/install-sh
gplflash-0.4.13/depcomp
gplflash-0.4.13/lib/
gplflash-0.4.13/lib/Makefile.in
gplflash-0.4.13/lib/Makefile.am
gplflash-0.4.13/lib/adpcm.cc
gplflash-0.4.13/lib/adpcm.h
gplflash-0.4.13/lib/bitmap.cc
gplflash-0.4.13/lib/bitmap.h
gplflash-0.4.13/lib/button.cc
gplflash-0.4.13/lib/button.h
gplflash-0.4.13/lib/character.cc
gplflash-0.4.13/lib/character.h
gplflash-0.4.13/lib/cxform.cc
gplflash-0.4.13/lib/cxform.h
gplflash-0.4.13/lib/displaylist.cc
gplflash-0.4.13/lib/displaylist.h
gplflash-0.4.13/lib/flash.cc
gplflash-0.4.13/lib/flash.h
gplflash-0.4.13/lib/font.cc
gplflash-0.4.13/lib/font.h
gplflash-0.4.13/lib/graphic.cc
gplflash-0.4.13/lib/graphic.h
gplflash-0.4.13/lib/graphic16.cc
gplflash-0.4.13/lib/graphic16.h
gplflash-0.4.13/lib/graphic24.cc
gplflash-0.4.13/lib/graphic24.h
gplflash-0.4.13/lib/graphic32.cc
gplflash-0.4.13/lib/graphic32.h
gplflash-0.4.13/lib/matrix.cc
gplflash-0.4.13/lib/matrix.h
gplflash-0.4.13/lib/movie.cc
gplflash-0.4.13/lib/movie.h
gplflash-0.4.13/lib/program.cc
gplflash-0.4.13/lib/program.h
gplflash-0.4.13/lib/rect.h
gplflash-0.4.13/lib/script.cc
gplflash-0.4.13/lib/script.h
gplflash-0.4.13/lib/shape.cc
gplflash-0.4.13/lib/shape.h
gplflash-0.4.13/lib/sound.cc
gplflash-0.4.13/lib/sound.h
gplflash-0.4.13/lib/sprite.cc
gplflash-0.4.13/lib/sprite.h
gplflash-0.4.13/lib/sqrt.cc
gplflash-0.4.13/lib/swf.h
gplflash-0.4.13/lib/text.cc
gplflash-0.4.13/lib/text.h
gplflash-0.4.13/ltconfig
gplflash-0.4.13/missing
gplflash-0.4.13/mkinstalldirs
gplflash-0.4.13/player/
gplflash-0.4.13/player/Makefile.in
gplflash-0.4.13/player/Makefile.am
gplflash-0.4.13/player/main.c
gplflash-0.4.13/player/vroot.h
gplflash-0.4.13/plugin/
gplflash-0.4.13/plugin/Makefile.in
gplflash-0.4.13/plugin/Makefile.am
gplflash-0.4.13/plugin/jri.h
gplflash-0.4.13/plugin/jri_md.h
gplflash-0.4.13/plugin/jritypes.h
gplflash-0.4.13/plugin/npapi.h
gplflash-0.4.13/plugin/npunix.c
gplflash-0.4.13/plugin/npupp.h
gplflash-0.4.13/plugin/plugin.c
gplflash-0.4.13/config.guess
gplflash-0.4.13/config.sub
gplflash-0.4.13/ltmain.sh
gplflash-0.4.13/aclocal.m4
gplflash-0.4.13/config.h.in
gplflash-0.4.13/Makefile.in
gplflash-0.4.13/configure
kyle@fast64:~$ cd gplflash-0.4.13
kyle@fast64:~/gplflash-0.4.13$ ./configure --with-plugin-dir=/usr/lib/mozilla/plugins/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for jpeg_destroy_decompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for X... libraries /usr/X11R6/lib, headers
checking for XOpenDisplay in -lX11... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking for mad_frame_decode in -lmad... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
Mozilla plugin will be placed in /usr/lib/mozilla/plugins/
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating player/Makefile
config.status: creating plugin/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
kyle@fast64:~/gplflash-0.4.13$
kyle@fast64:~/gplflash-0.4.13$ make
make  all-recursive
make[1]: Entering directory `/home/kyle/gplflash-0.4.13'
Making all in lib
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/lib'
Making all in player
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/player'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/player'
Making all in plugin
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/plugin'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/plugin'
make[2]: Entering directory `/home/kyle/gplflash-0.4.13'
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13'
make[1]: Leaving directory `/home/kyle/gplflash-0.4.13'
kyle@fast64:~/gplflash-0.4.13$
kyle@fast64:~/gplflash-0.4.13$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
Making install in lib
make[1]: Entering directory `/home/kyle/gplflash-0.4.13/lib'
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/lib'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libflash.la' '/usr/local/lib/libflash.la'
/usr/bin/install -c .libs/libflash.so.0.13.0 /usr/local/lib/libflash.so.0.13.0
(cd /usr/local/lib && rm -f libflash.so.0 && ln -s libflash.so.0.13.0 libflash.so.0)
(cd /usr/local/lib && rm -f libflash.so && ln -s libflash.so.0.13.0 libflash.so)/usr/bin/install -c .libs/libflash.lai /usr/local/lib/libflash.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'flash.h' '/usr/local/include/flash.h'
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/lib'
make[1]: Leaving directory `/home/kyle/gplflash-0.4.13/lib'
Making install in player
make[1]: Entering directory `/home/kyle/gplflash-0.4.13/player'
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/player'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'swfplayer' '/usr/local/bin/swfplayer'
/usr/bin/install -c .libs/swfplayer /usr/local/bin/swfplayer
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/player'
make[1]: Leaving directory `/home/kyle/gplflash-0.4.13/player'
Making install in plugin
make[1]: Entering directory `/home/kyle/gplflash-0.4.13/plugin'
make[2]: Entering directory `/home/kyle/gplflash-0.4.13/plugin'
make[2]: Nothing to be done for `install-exec-am'.
mkdir -p "/usr/lib/mozilla/plugins/"
cp ./.libs/libnpflash.so.0.0.0 "/usr/lib/mozilla/plugins//libnpflash.so"
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13/plugin'
make[1]: Leaving directory `/home/kyle/gplflash-0.4.13/plugin'
make[1]: Entering directory `/home/kyle/gplflash-0.4.13'
make[2]: Entering directory `/home/kyle/gplflash-0.4.13'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kyle/gplflash-0.4.13'
make[1]: Leaving directory `/home/kyle/gplflash-0.4.13'

======================== Installation succesful ==========================

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK


*** Warning: The package name "gplflash-0.4.13" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values:

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ Package created with checkinstall 1.5.3 ]
2 -  Name:    [ gplflash-0.4.13 ]
3 -  Version: [ 0.4.13 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ gplflash-0.4.13 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue: ^[[1~

*** Warning: The package name "gplflash-0.4.13" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values:

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ Package created with checkinstall 1.5.3 ]
2 -  Name:    [ gplflash-0.4.13 ]
3 -  Version: [ 0.4.13 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ gplflash-0.4.13 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue: 7
Enter the architecture type:
>> amd64

*** Warning: The package name "gplflash-0.4.13" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values:

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ Package created with checkinstall 1.5.3 ]
2 -  Name:    [ gplflash-0.4.13 ]
3 -  Version: [ 0.4.13 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ gplflash-0.4.13 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue:

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to
 /home/kyle/gplflash-0.4.13/gplflash-0.4.13_0.4.13-1_amd64.deb

 You can remove it from your system anytime using:

      dpkg -r gplflash-0.4.13

**********************************************************************

kyle@fast64:~/gplflash-0.4.13$




thats what happened when i installed

---

### Post by catlett on 2006-05-16
> Done. The new package has been installed and saved to
/home/kyle/gplflash-0.4.13/gplflash-0.4.13_0.4.13-1_amd64.deb
That looks to me like it installed. Do you not have flash when running firefox still? I assume you closed firefox and restarted. 
I didn't read the how to but are you supposed to put a link to these libraries from firefox's plug-ins? > If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
- add LIBDIR to the `LD_LIBRARY_PATH' environment variable
during execution
- add LIBDIR to the `LD_RUN_PATH' environment variable
during linking
- use the `-Wl,--rpath -Wl,LIBDIR' linker flag
- have your system administrator add LIBDIR to `/etc/ld.so.con Just a thought. I googled around and most people think you can't install flash to amd64 so you're ahead of them which is good but there is no other source for help which is bad.

---

### Post by avidsensei on 2006-05-16
wow maby i should just restart and install a 32 bit ubuntu..... yeah so how do you do  the linking thing?

---

### Post by catlett on 2006-05-16
Sorry I don't know. That is an excerpt from your terminal output. A link to other libraries is how I understood it, but I don't know how to do it. If you want to know your not alaone in your frustration with adobe browse this [http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm](http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm)

---

### Post by avidsensei on 2006-05-16
any ideas?

---

### Post by indie56 on 2006-08-09
Refer post #9.
I am totally new to Ubuntu. I have downloaded the file, dragged into the Home folder, right clicked and chosen 'extract here'. A file install_flash_player_7_linux is created. When I open my Terminal, I get  'inderpaldeol@deol-desktop:~$'. 
How do I run the command  cd  /install_flash_player_7-linux  ? 
Please give me detailed instruction in steps. I am a total novice.

Thanks.

---

