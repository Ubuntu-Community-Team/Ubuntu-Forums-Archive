---
title: "Cinepaint"
date: 2008-05-24
forum: Art &amp; Design
---

### Post by Eurospike on 2008-05-24
I noticed how difficult it appeared to be to get an Ubuntu Version for Cinepaint for new people such as myself, so instead of using a .tar.gz, I converted them to .deb and uploaded them to here:

[http://www.4shared.com/dir/7238897/57d3986b/sharing.html](http://www.4shared.com/dir/7238897/57d3986b/sharing.html)

Those files are necessary to enable it to run, it worked on an Ubuntu 8.04 I installed yesterday, so I presume it should work on most people's Ubuntu's.

Warning to all, if it will not run from the menu, try typing in "cinepaint" in the terminal to find the errors you have, as then it is possible to fix rather than a "It's not working, why?"

---

### Post by p221072 on 2008-06-03
I don't understand what you mean...
I've installed **Cinepaint** just from the Applications > Add/Remove and it seems to be working fine.

---

### Post by Eurospike on 2008-06-08
How strange, I just checked both the Add and remove, and the package manager, and the only one found in the package manager is the one I converted from Alien.
I have most of the various repositories available, so I have no idea how you came about to such a thing, however I am using 8.04 which I installed 3 weeks before. Unless a new version has come out that has the repository with Cinepaint, I can only suggest that you be slightly more informative in how you managed it.

---

### Post by Tigin on 2008-07-07
QQ... when i tried to install it , it said ** wrong architecture** 

Any chance to find an AMD64 package ?




(My system : AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

---

### Post by AJB2K3 on 2008-07-08
Have you tryed going to its website and downloading the .debs from there?

---

### Post by Tigin on 2008-07-08
I ve tried 1st their site then checked forums , there are no deb packages in there only some platform independent tar.gz files , i could not make them deb .   QQ


(My system : AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

---

### Post by lyceum on 2008-07-08
> **p221072 said:**
> I don't understand what you mean...
I've installed **Cinepaint** just from the Applications > Add/Remove and it seems to be working fine.

What version of Ubuntu are you running? It is not in my add/remove???

:confused:

---

### Post by Sean4000 on 2008-07-09
I'm on 64bit hardy Heron and it is not there.  This is fishy, please help, this is a great program and I cannot go back to 7.10 which had it because of my 8800GT vide0 card.

---

### Post by p221072 on 2008-07-21
> **lyceum said:**
> What version of Ubuntu are you running? It is not in my add/remove???

:confused:

I'm running Ubuntu 7.10 but I guess it depends on the repository, you need to enable the *universe *if it is not.
Check out this: [http://linuxappfinder.com/package/cinepaint](http://linuxappfinder.com/package/cinepaint)

---

### Post by AJB2K3 on 2008-07-21
> **Sean4000 said:**
> I'm on 64bit hardy Heron and it is not there.  This is fishy, please help, this is a great program and I cannot go back to 7.10 which had it because of my 8800GT vide0 card.
Its an I386 package so you'll probably have to compile it from source.

---

### Post by lyceum on 2008-07-21
> **p221072 said:**
> I'm running Ubuntu 7.10 but I guess it depends on the repository, you need to enable the *universe *if it is not.
Check out this: [http://linuxappfinder.com/package/cinepaint](http://linuxappfinder.com/package/cinepaint)

I am running 8.04 with Universe enabled and it is still not there :(

---

### Post by Tigin on 2008-07-21
I think it was on ubuntu studio repos , not exactly sure tho...

I am using cinepaint + cinerella on my desktop under PClinuxOS DFE

---

### Post by dmn_clown on 2008-07-22
> **lyceum said:**
> I am running 8.04 with Universe enabled and it is still not there :(

GTK1 is no longer supported by Debian and has been removed along with all programs that depend on it hence no Cinepaint in Ubuntu.  You can always compile it yourself just remember to configure it to use GTK2.

---

### Post by lyceum on 2008-07-23
> **dmn_clown said:**
> GTK1 is no longer supported by Debian and has been removed along with all programs that depend on it hence no Cinepaint in Ubuntu.  You can always compile it yourself just remember to configure it to use GTK2.

Will Cinepaint be making a package Debian based OSs can use?

---

### Post by dmn_clown on 2008-07-23
> **lyceum said:**
> Will Cinepaint be making a package Debian based OSs can use?

There is a Sidux developer that is currently going through the bureaucracy to become a Debian Developer to package Cinepaint (the original maintainer disappeared), you can find them here:  [http://sidux.net/etorix/](http://sidux.net/etorix/)

---

### Post by lyceum on 2008-07-23
> **dmn_clown said:**
> There is a Sidux developer that is currently going through the bureaucracy to become a Debian Developer to package Cinepaint (the original maintainer disappeared), you can find them here:  [http://sidux.net/etorix/](http://sidux.net/etorix/)

Cool, thanks!

---

### Post by rocknrolf77 on 2008-08-31
Thank's for the packages. Wondered where cinepaint had gone.

---

### Post by AJB2K3 on 2008-08-31
Well I found a 2.2.5 deb on there homesite.

---

### Post by anachronon on 2008-09-13
> **eurospike said:**
> i noticed how difficult it appeared to be to get an ubuntu version for cinepaint for new people such as myself, so instead of using a .tar.gz, i converted them to .deb and uploaded them to here:

[http://www.4shared.com/dir/7238897/57d3986b/sharing.html](http://www.4shared.com/dir/7238897/57d3986b/sharing.html)

those files are necessary to enable it to run, it worked on an ubuntu 8.04 i installed yesterday, so i presume it should work on most people's ubuntu's.

Warning to all, if it will not run from the menu, try typing in "cinepaint" in the terminal to find the errors you have, as then it is possible to fix rather than a "it's not working, why?"

I installed Cinepaint from the .deb package, but when I tried to run it, it wouldn't run.  The response I got from the terminal is:

```
cinepaint: error while loading shared libraries:
liboyranos.so.0.1.7: cannot open shared object file: No such file or directory
```

Does anyone know what this means, or what I should do?  Obviously, I need a file, or folder.  but, which one, where do I get it, and where do I install it?

---

### Post by lyceum on 2008-09-15
> **anachronon said:**
> I installed Cinepaint from the .deb package, but when I tried to run it, it wouldn't run.  The response I got from the terminal is:

```
cinepaint: error while loading shared libraries:
liboyranos.so.0.1.7: cannot open shared object file: No such file or directory
```

Does anyone know what this means, or what I should do?  Obviously, I need a file, or folder.  but, which one, where do I get it, and where do I install it?

As stated above: GTK1 is no longer supported by Debian so, no Cinepaint on Ubuntu. You would have to compile it yourself and use GTK1.

---

### Post by HappyHenry on 2008-09-15
> **dmn_clown said:**
> There is a Sidux developer that is currently going through the bureaucracy to become a Debian Developer to package Cinepaint (the original maintainer disappeared), you can find them here:  [http://sidux.net/etorix/](http://sidux.net/etorix/)

I used the link. The instructions seem a little cryptic to this noob. I went to, System->Administration->Software Sources->Third Party Software->Add->
Under this I added, deb [http://sidux.net/etorix/i386](http://sidux.net/etorix/i386) ./ and deb-src [http://sidux.net/etorix/i386](http://sidux.net/etorix/i386) ./ 
(I'm running 32bit system)

When I click Close I get the msg, "The information about available software is out-of-date"
I click, "reload."
I get msg, "W: GPG error: [http://sidux.net](http://sidux.net) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00BD6279A514E9F"

Now this is the problem. I dont know how to get that, "key" where it belongs. I looked under Authentication and see there are Keys there but dont know what exactly to add, what is the key.
I see on the website, "Get the key:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9A514E9F && apt-key add /root/.gnupg/pubring.gpg"
I thought this was a command for terminal so thats what I tried. I received,
 "me@me-laptop:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9A514E9F && apt-key add /root/.gnupg/pubring.gpg
gpg: requesting key 9A514E9F from hkp server wwwkeys.eu.pgp.net
gpg: key 9A514E9F: "Aedan Kelly <etorix@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gpg: [COLOR="Red"]can't open `/root/.gnupg/pubring.gpg': No such file or directory"[/COLOR]
THIS IS WHERE I STOPPED. I HAVEN'T DONE ANYTHING ELSE. NEED HELP.
--------------------------------------------------------------------
Now I'm thinking I need a file/directory called, ???? under the root directory. If this is true I am not sure if it would be under, _root_ create a file called _gnupg_ and then in that a file called _pubring_ and under that a file called _gpg_.
I hope you can understand what I have done, what I have missed and what I can do to get CinePaint working.
I see the other entries saying it's for GTK1 and Hardy Heron uses GTK2. I thought this version of CinePaint was modified for GTK2.
If I am totally messed up in my thoughts with this do I have to do anything more than just clear the repositories from my Soft Sorces. The terminal command didn't really do anything, because of the error, right?
Thank you if you can help me in any way. If I need to clarify anything let me know. Thank you.
--------------------------EDIT!!!!---------------------------------------
Okay, I kept trying. I see in the instructions the steps are a little out of sequence. Just after the step,
#
Get the key:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9A514E9F && apt-key add /root/.gnupg/pubring.gpg
there are the steps, "First get...
So I tried those steps and TADA! it's started up. I haven't used it yet and saved any work but it is listed in my Applications and does open when i click to run it.
Sorry for the confussion and I will leave the post in case anyone else has the same problem. Please tell me im not the only. "slow one in class." 
**[COLOR="Red"]Thank you for the link and it does work well for Hardy Heron 32 bit.[/COLOR]**
Edit number two--------
It works fine. Save file and open again, rework, save etc.. 
Does anyone else have it working. Are there files I could post that would help others. I dont know why It works for me and so many say it cant be done, but it does. So if i can post anything more to help let me know and i will post.

---

### Post by Offoffoff on 2009-01-16
But that link does not work at Itrepid Ibex due dependency problems... How to compile cinepaint for Intrepid Ibex? I have done all I have to do. But when I make:
./configure --enable-gtk2
make
- I find myself here:
make[3]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/home/ivan/cinepaint-0.22-1/plug-ins/icc_examin/icc_examin'
Compiling flstring.c ...
Compiling vsnprintf.c ...
Compiling agviewer.cpp ...
In file included from icc_profile.h:35,
                 from icc_kette.h:35,
                 from icc_examin.h:35,
                 from agviewer.cpp:17:
icc_helfer.h:186: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: ‘typedef’ &#1074; &#1101;&#1090;&#1086;&#1081; &#1076;&#1077;&#1082;&#1083;&#1072;&#1088;&#1072;&#1094;&#1080;&#1080; &#1086;&#1090;&#1073;&#1088;&#1086;&#1096;&#1077;&#1085;
In file included from icc_profile.h:39,
                 from icc_kette.h:35,
                 from icc_examin.h:35,
                 from agviewer.cpp:17:
icc_profile_header.h: In member function ‘void ICCheader::set_magic()’:
icc_profile_header.h:99: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: deprecated conversion from string constant to ‘char*’
icc_profile_header.h: In member function ‘void ICCheader::set_manufacturer()’:
icc_profile_header.h:121: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: deprecated conversion from string constant to ‘char*’
icc_profile_header.h: In member function ‘void ICCheader::set_model()’:
icc_profile_header.h:127: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: deprecated conversion from string constant to ‘char*’
icc_profile_header.h: In member function ‘void ICCheader::set_creator()’:
icc_profile_header.h:167: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: deprecated conversion from string constant to ‘char*’
In file included from icc_examin.h:36,
                 from agviewer.cpp:17:
icc_oyranos.h: At global scope:
icc_oyranos.h:153: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘byte’
icc_oyranos.h:153: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘kanaele’
icc_oyranos.h:164: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘byte’
icc_oyranos.h:164: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘kanaele’
icc_oyranos.h:176: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘byte’
icc_oyranos.h:176: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘kanaele’
icc_oyranos.h:194: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘byte’
icc_oyranos.h:194: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#1073;&#1086;&#1083;&#1077;&#1077; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1089; &#1080;&#1084;&#1077;&#1085;&#1077;&#1084; ‘kanaele’
In file included from agviewer.cpp:17:
icc_examin.h:50: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: declaration ‘class icc_examin_ns::EinModell’ does not declare anything
make[3]: *** [agviewer.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[3]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/ivan/cinepaint-0.22-1/plug-ins/icc_examin/icc_examin'
make[2]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/ivan/cinepaint-0.22-1/plug-ins/icc_examin'
make[1]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/ivan/cinepaint-0.22-1/plug-ins'
make: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
What am I have to do?

---

### Post by muckblit on 2009-05-25
[http://www.cinepaint.org/docs/download.html](http://www.cinepaint.org/docs/download.html)

ubuntu-cvs.sh ----

[http://cinepaint.cvs.sourceforge.net/viewvc/*checkout*/cinepaint/cinepaint-project/cinepaint/ubuntu-cvs.sh?content-type=text/plain](http://cinepaint.cvs.sourceforge.net/viewvc/*checkout*/cinepaint/cinepaint-project/cinepaint/ubuntu-cvs.sh?content-type=text/plain)

echo ubuntu-cvs.sh - install from CVS source on ubuntu
echo Copyright 10.19.2008 [email]Robin.Rowe@cinepaint.org[/email]
echo License BSD
echo INSTRUCTIONS: This script downloads and builds CinePaint from CVS.
echo If you are a member of the CinePaint dev team, you want cvs-dev.sh
echo Expect it to take hours to download and build cinepaint from scratch.
echo Fetching cinepaint from SourceForge CVS...
mkdir cvs
cd cvs
echo Press [Enter] when prompted for CVS password...
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/cinepaint login
cvs -z3 -d:pserver:anonymous@cinepaint.cvs.sourceforge.net:/cvsroot/cinepaint co cinepaint-project
cd cinepaint-project/cinepaint/
echo Installing build tools and libraries...
echo Enter root password to install apt-get packages...
sudo apt-get install gcc automake g++ libfltk1.1-dev libgtk2.0-dev zlib1g-dev libjpeg62-dev libpng12-dev libtiff4-dev libopenexr-dev libxpm-dev libgutenprint-dev libgutenprintui2-dev liblcms1-dev pkg-config ftgl-dev libxmu-dev libxxf86vm-dev flex python-dev libtool
echo Building cinepaint...
sh autogen.sh
./configure
make
echo Enter root password to install cinepaint...
sudo make install
echo Running cinepaint...
export LD_LIBRARY_PATH=/usr/lib/local
cinepaint
echo Don't forget to add LD_LIBRARY_PATH=/usr/lib/local to your profile...

---

### Post by bioalchemist on 2009-06-13
for me, the above script worked, but not completely.  I had to do a couple of things to get it to work.  First, obviously, you need cvs installed. ```
sudo apt-get install cvs
``` Also, the install stopped after the login line and would not continue, so when I deleted that line, it continued.

Second, at the end, cinepaint installed but would not run, so i had to
```
sudo ldconfig
```
then cinepaint ran just fine.

---

### Post by disx on 2009-07-05
i got that script from the cinepaint site, but it didn't say anything about CVS and all that. i had already downloaded the tar file so do i not need to do the CVS bit? sorry i'm a nub.

i did this:

sudo apt-get install gcc automake g++ libfltk1.1-dev libgtk2.0-dev zlib1g-dev libjpeg62-dev libpng12-dev libtiff4-dev libopenexr-dev libxpm-dev libgutenprint-dev libgutenprintui2-dev liblcms1-dev pkg-config ftgl-dev libxmu-dev libxxf86vm-dev flex python-dev libtool

and it seemed to work fine,
but then i tried sh autogen.sh
and it said Can't open autogen.sh
so i looked around the net and found out i should do sudo sh autogen.sh
that didn't work either.
same response: Can't open autogen.sh

any ideas? thanks!

---

### Post by jorx on 2009-08-16
I have the same problem as **disx**.

This is somewhat serious- as Photoshop is one the biggest holes in my migration to Linux. I absolutely need floating point image support !

I'm also a somewhat noob.  I've tried both the .deb files (which claim a missing dependency: libcinepaint0 which I cannot find ) and also the cvs method which gives me "cannot find autogen.sh".

Running the ./configure manually on the tar.gz gives me 

```
=================================================================
              Configuration Results

GTK CinePaint Version 0.22-1


General dependencies:
./configure: line 29441: gtk-config: command not found
   Gtk1 toolkit                 yes
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.18
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 1.6.1
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.27
   Jpeg plug-in:                yes
   Print plug-in:               no
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     yes    iol
=================================================================

configure: error: !!! An ERROR occured !!!
    Please check the above messages to see why.
    For bug reports please include the complete above output.

```

---

### Post by eyeJ on 2009-12-28
> **jorx said:**
> I have the same problem as **disx**.

This is somewhat serious- as Photoshop is one the biggest holes in my migration to Linux. I absolutely need floating point image support !

I'm also a somewhat noob.  I've tried both the .deb files (which claim a missing dependency: libcinepaint0 which I cannot find ) and also the cvs method which gives me "cannot find autogen.sh".

Running the ./configure manually on the tar.gz gives me 

```
=================================================================
              Configuration Results

GTK CinePaint Version 0.22-1


General dependencies:
./configure: line 29441: gtk-config: command not found
   Gtk1 toolkit                 yes
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.18
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 1.6.1
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.27
   Jpeg plug-in:                yes
   Print plug-in:               no
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     yes    iol
=================================================================

configure: error: !!! An ERROR occured !!!
    Please check the above messages to see why.
    For bug reports please include the complete above output.

```

To get rid of that error you need al the plug-ins like Oyranos, Python, print plug-in... It should compile without them if I am not mistaking but to be on the safe side I downloaded and compiled all that were missing from the Synaptic. (don't take my word for it I am not an expert)
I managed to compile cinepaint a while back in Ubuntu 9.04 but I have no luck with 9.10. I get some recursive error leaving plugins/... directory. I can't figure out what to do to fix it.

---

### Post by szr4321 on 2010-12-14
Just in case someone is still interested in this: for the source tar ball (without the CVS script which I couldn't find unfortunately) I made a small patch, see [http://lglinux.blogspot.com/2010/12/compiling-cinepaint-on-ubuntu-maverick.html]("http://lglinux.blogspot.com/2010/12/compiling-cinepaint-on-ubuntu-maverick.html").

---

