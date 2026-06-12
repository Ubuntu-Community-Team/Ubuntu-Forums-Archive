---
title: "Ubuntu: Installing and Running gTwitter!"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-22
Everything was based from here:

```
karlo@karlo-laptop:~/Desktop/gtwitter-1.0beta$ sudo apt-cache search Mono Development
libslang2-dev - The S-Lang programming library, development version
libxpm-dev - X11 pixmap library (development headers)
python-all-dbg - Package depending on all supported Python debugging packages
python-all-dev - Package depending on all supported Python development packages
libmono-cecil0.5-cil - library to generate and inspect CIL assemblies
libslang1-dev - The S-Lang programming library, development version
libslang1-utf8-dev - The S-Lang programming library, development version with utf8 support
mono-tools-devel - Various development tools for mono
monodevelop - C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment
qyoto-dev-tools - Development tools for Qt 4 bindings for Mono C# CLI
qyoto-examples - Development tools for Qt 4 bindings for Mono C# CLI
sineshaper - Monophonic synth plugin with two oscillators and waveshapers
stetic - GNOME and GTK+ GUI designer
ttf-inconsolata - monospace font for pretty code listings and for the terminal
libmono-dev - libraries for the Mono JIT - Development files
mono-devel - Mono CLI runtime with development tools
mono-mcs - Mono C# compiler
karlo@karlo-laptop:~/Desktop/gtwitter-1.0beta$ sudo apt-get install mono-mcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmono-peapi1.0-cil libmono-relaxng1.0-cil libmono-system-runtime1.0-cil
The following NEW packages will be installed:
  libmono-peapi1.0-cil libmono-relaxng1.0-cil libmono-system-runtime1.0-cil
  mono-mcs
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 833kB of archives.
After unpacking 2826kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com gutsy-security/main libmono-peapi1.0-cil 1.2.4-6ubuntu6.1 [44.0kB]
Get:2 http://security.ubuntu.com gutsy-security/main libmono-relaxng1.0-cil 1.2.4-6ubuntu6.1 [83.3kB]
Get:3 http://security.ubuntu.com gutsy-security/main libmono-system-runtime1.0-cil 1.2.4-6ubuntu6.1 [60.5kB]
Get:4 http://security.ubuntu.com gutsy-security/main mono-mcs 1.2.4-6ubuntu6.1 [645kB]
Fetched 833kB in 21s (39.4kB/s)                                                
Selecting previously deselected package libmono-peapi1.0-cil.
(Reading database ... 136992 files and directories currently installed.)
Unpacking libmono-peapi1.0-cil (from .../libmono-peapi1.0-cil_1.2.4-6ubuntu6.1_all.deb) ...
Selecting previously deselected package libmono-relaxng1.0-cil.
Unpacking libmono-relaxng1.0-cil (from .../libmono-relaxng1.0-cil_1.2.4-6ubuntu6.1_all.deb) ...
Selecting previously deselected package libmono-system-runtime1.0-cil.
Unpacking libmono-system-runtime1.0-cil (from .../libmono-system-runtime1.0-cil_1.2.4-6ubuntu6.1_all.deb) ...
Selecting previously deselected package mono-mcs.
Unpacking mono-mcs (from .../mono-mcs_1.2.4-6ubuntu6.1_all.deb) ...
Setting up libmono-peapi1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-relaxng1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-system-runtime1.0-cil (1.2.4-6ubuntu6.1) ...
Setting up mono-mcs (1.2.4-6ubuntu6.1) ...

karlo@karlo-laptop:~/Desktop/gtwitter-1.0beta$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... /usr/bin/mcs
checking pkg-config is at least version 0.9.0... yes
checking for MONO_CAIRO... yes
checking for GTK_SHARP_20... yes
checking for GNOME_VFS_SHARP_20... yes
checking for GLIB_SHARP_20... yes
checking for GCONF_SHARP_20... yes
configure: creating ./config.status
config.status: creating gtwitter/Makefile
config.status: creating gtwitter/gtwitter
config.status: creating Makefile
karlo@karlo-laptop:~/Desktop/gtwitter-1.0beta$ make
Making all in gtwitter
make[1]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
mkdir -p ./bin/Release
cp 'gtwitter' 'bin/Release/gtwitter'
mkdir -p ./bin/Release/
mcs -noconfig -codepage:utf8 -unsafe -warn:4 -out:bin/Release/gtwitter.exe -target:exe './gtk-gui/generated.cs' './MainWindow.cs' './Main.cs' './AssemblyInfo.cs' './gtk-gui/gtwitter.MainWindow.cs' './PreferencesWindow.cs' './gtk-gui/gtwitter.PreferencesWindow.cs' './ReadInfo.cs' './GetTwitterData.cs' './PostToTwitter.cs' './CompositeInterface.cs' './AboutDialog.cs' './libsexy/UrlActivatedHandler.cs' './libsexy/UrlLabel.cs' './libsexy/IconEntry.cs' './libsexy/IconEntryPosition.cs' './libsexy/IconPressedHandler.cs' './libsexy/IconReleasedHandler.cs'  '-resource:./gtk-gui/gui.stetic' '-resource:./../data/gtwitter-22.png' '-resource:./../data/gtwitter-48.png' '-resource:./../data/gtwitter-64.png' -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp-peditors.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/mono/1.0/Mono.Cairo.dll   -r:System -r:System.Xml -r:Mono.Posix -r:System.Web  
./libsexy/UrlLabel.cs(60,37): warning CS0169: The private method `Sexy.UrlLabel.OverrideUrlActivated(GLib.GType)' is never used
./libsexy/IconEntry.cs(61,37): warning CS0169: The private method `Sexy.IconEntry.OverrideIconPressed(GLib.GType)' is never used
./libsexy/IconEntry.cs(126,37): warning CS0169: The private method `Sexy.IconEntry.OverrideIconReleased(GLib.GType)' is never used
Compilation succeeded - 3 warning(s)
make[1]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
make[1]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta'
karlo@karlo-laptop:~/Desktop/gtwitter-1.0beta$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@karlo-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ gtwitter ]
3 -  Version: [ 1.0beta ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gtwitter-1.0beta ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in gtwitter
make[1]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
make[2]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c './bin/Release/gtwitter' '/usr/bin/gtwitter'
/usr/bin/install: setting permissions for `/usr/bin/gtwitter': No such file or directory
test -z "/usr/lib/gtwitter" || /bin/mkdir -p "/usr/lib/gtwitter"
 /usr/bin/install -c './bin/Release/gtwitter.exe' '/usr/lib/gtwitter/gtwitter.exe'
/usr/bin/install: setting permissions for `/usr/lib/gtwitter/gtwitter.exe': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
make[1]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta/gtwitter'
make[1]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta'
make[2]: Entering directory `/home/karlo/Desktop/gtwitter-1.0beta'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta'
make[1]: Leaving directory `/home/karlo/Desktop/gtwitter-1.0beta'

======================== Installation successful ==========================

Copying documentation directory...
./
./README
./INSTALL
./ChangeLog
./COPYING
grep: /var/tmp/aDmPrRYhGIBTehnVNIrqH/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/karlo/Desktop/gtwitter-1.0beta/gtwitter_1.0beta-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r gtwitter

**********************************************************************
```

First, of course extract the .tar file into some folder.
Second, according to [http://code.google.com/p/gtwitter/](http://code.google.com/p/gtwitter/) it needs some Dependencies.
Third, I searched Aptitude for the Mono library etc.. and probably I haven't installed the other **Dependencies** that's why the program won't run.
Fourth, run ./configure OR ./configure --prefix=/usr ([http://code.google.com/p/gtwitter/](http://code.google.com/p/gtwitter/))
Fifth, of course run make
Sixth, instead of using make install, I used sudo checkinstall, tutorial from [http://ubuntuforums.org/showpost.php?p=7458&postcount=1](http://ubuntuforums.org/showpost.php?p=7458&postcount=1) that's why I included the .deb file as an attachment for you to test it, if this thing works on your PC.
Seventh, I reinstalled the program, don't know why it says that it's already installed.
Eighth, tell me what you think, why **i can't run** the program.

An alternative, an old program to use is **Twitux**, but I think the program is old, so I am curious with PwyTwitter... [http://www.pwytter.com](http://www.pwytter.com) can someone guide me how to install it?

Oh yeah, this site is useful: [http://www.getdeb.net/app/gTwitter](http://www.getdeb.net/app/gTwitter) and [http://www.getdeb.net/app/Twitux](http://www.getdeb.net/app/Twitux)

**To remove gTwitter**

Terminal:

```
sudo dpkg -r gtwitter
```
```
sudo apt-get remove  libmono-peapi1.0-cil libmono-relaxng1.0-cil libmono-system-runtime1.0-cil
  mono-mcs
```

THERE! **removed**!

---

### Post by chlorinekid on 2008-03-23
it's in the repositories, i just used: 

```
sudo apt-get install gtwitter
```

worked fine. maybe just try that instead if compiling it yourself?

---

### Post by karlo on 2008-03-24
> **chlorinekid said:**
> it's in the repositories, i just used: 

```
sudo apt-get install gtwitter
```

worked fine. maybe just try that instead if compiling it yourself?

How? The traditional way? ./configure and then make then make install?

---

