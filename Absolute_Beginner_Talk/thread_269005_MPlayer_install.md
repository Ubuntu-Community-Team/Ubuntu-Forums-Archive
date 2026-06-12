---
title: "MPlayer install"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by bobknab on 2006-10-01
bob here new to linux ubuntu ----------------
What do i need to do to download and install
MPlayer - thanks bobknab

---

### Post by aysiu on 2006-10-01
I think you need to read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by bobknab on 2006-10-01
Thanks aysiu

i tried to install Mplayer from the terminal it was downloaded to the Desktop
and i got this reply

-d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
bobknab@bob:~$

this is a lot of stuff so where to go from here 

/home/bobknab/Desktop/MPlayer-1.0pre8 

/home/bobknab/Desktop/Screenshot-1.png

Thanks bob knab

---

### Post by uk_sphinx on 2006-10-01
yeah i dont understand manually installing downloads from desktop either.
i always get reports of directory or file dosnt exist.
the psychocats tutorial dosnt explain it clear enough to get it through my thick head.

any more tutorials you want me to know about aysiu??

---

### Post by keheikev on 2006-10-01
Since Ive spent the better part of the week installing and uninstalling mplayer because of a version conflict of the mozilla -mplayer plugin may I offer in addition to aysiu's instructions a simple way to just install it is to go to system/applications/synaptic enter your password and search for mplayer. Select mplayer for installation.
 If you need help with the plugin the program that allows you to stream within a firefox browser window let us know.
Kiheikev
:KS

---

### Post by bobknab on 2006-10-02
Thanks there is no synaptic myplayer  package that i could locate
i went to – ubuntu.secs.oakland.edu – and downloaded 
the myplayer package and got ---------------------------------------------------------

              opened with the package installer
           Error – Dependency is not satisfiable: libfacc0 

The Ultimate Movie Player For Linux
It plays most mpeg, avi and asf files, supported by many native and win32 DLL codecs. You can watch VCD, DVD and even DivX movies too. The other big feature of mplayer is the wide range of supported output drivers. It works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev, but you can use SDL (and this way all drivers of SDL) and some lowlevel card-specific drivers (for Matrox/3dfx/SiS) too! Most of them supports software or hardware scaling, so you can enjoy movies in fullscreen.
This version includes the Gtk GUI 

   -----------------------------------------------------------------------------------------------------

  i have no idea at this time what the message is saying -
 bob knab -------------------------------------------------------------

---

### Post by garybrlow on 2006-10-02
You are better off compiling Mplayer. Download the source tarball from [http://www.mplayerhq.hu](http://www.mplayerhq.hu) (official site). Read the documentation and FAQ first then make sure you have the win32 codecs installed xorg dev libraries plus the other dependencies stated the install/readme in the tarball. Follow the compile instructions including the enable GUI option, set subtitle font and default skin, and whalla your're good to go. :)

Been using the compiled version for quite some time on a Xubuntu 6.60.1. :mrgreen: 

Cheers,
GaryBrlow

---

### Post by bobknab on 2006-10-02
bob-again

after looking arround i found this

Package Contents Search Results

You have searched for the contents of libfaac0 in dapper, architecture i386.
Package contains 7 files, displaying files 1 to 7.

FILE                                                       PACKAGE

usr/lib/libfaac.so.0					    libs/libfaac0 [multiverse]
usr/lib/libfaac.so.0.0.0				    libs/libfaac0 [multiverse]
usr/share/doc/libfaac0/README				    libs/libfaac0 [multiverse]
usr/share/doc/libfaac0/TODO				    libs/libfaac0 [multiverse]
usr/share/doc/libfaac0/changelog.Debian.gz		    libs/libfaac0 [multiverse]
usr/share/doc/libfaac0/changelog.gz			    libs/libfaac0 [multiverse]
usr/share/doc/libfaac0/copyright			    libs/libfaac0 
[multiverse]

i am thinking that this file could have a BUG in it but its only a thought
i am wondering if anny one has myplayer working and what did they do to
get it working ------------- bob knab

---

### Post by Phosphoric on 2006-10-02
I had a similar problem, couldn't find mplayer in the repostories.  I was put right here:  [http://www.ubuntuforums.org/showthread.php?t=264869](http://www.ubuntuforums.org/showthread.php?t=264869)

Good luck :)

---

### Post by anaconda on 2006-10-02
I installed mplayer from the repositories without any problems.. Cant see any point in compiling it yourself, unless if you want to practice compiling.. 

have you enabled all the repositories the reason you cant find it may be because you have not..
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by keheikev on 2006-10-02
Just to add to anacondas post yes I have mplayer up and working fine. I am thinking that in the case of a new user like me compiling an install is beyond my scope. You do have to enable the multiverse and universe etc.

---

