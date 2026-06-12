---
title: "Instaling Java and fash player on PPC????"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-04-29
I have java installed, however firefox does not think so or something..it says its not installed. I want to install some kiind of adobe flash substitute. everyone I found, there is missing too much to do t. Dnash i think it is, is missing a lot of things to do it so is one other one and what I am trying now is gplglash.....it wants libz...and I cannot find it in synaptic or online...what do i do???

---

### Post by avtolle on 2008-04-29
> **shgadwa said:**
> I have java installed, however firefox does not think so or something..it says its not installed. I want to install some kiind of adobe flash substitute. everyone I found, there is missing too much to do t. Dnash i think it is, is missing a lot of things to do it so is one other one and what I am trying now is gplglash.....it wants libz...and I cannot find it in synaptic or online...what do i do???
[http://ubuntuforums.org/showthread.php?t=754620&page=3](http://ubuntuforums.org/showthread.php?t=754620&page=3) see my post 22 on installing Java. If you have it downloaded and installed, then see the bit about the need for a symbolic link. On Flash, gnash seems to be the project with the most development. Unless there is a ppc version of Flash developed and released for Linux, there isn't going to be a straight substitute to "just plug in". I notice gnash works, albeit herky-jerky, on 8.04 with sound through the PulseAudio system.

---

### Post by shgadwa on 2008-04-29
This is what I need for gnash...and the package manager has hardly any of it....


Configured paths for powerpc-unknown-linux-gnu are:
        DocBook document processing disabled (default)
        ERROR: No libxml2 development package installed!
               To compile this project install
               or .deb users: apt-get install libxml2-dev
               or .rpm users: yum install libxml2-devel
        ERROR: No KDE development package installed!
               To disable the KDE gui,
               reconfigure using --enable-gui=<list-of-guis>
               and omit kde from the list.
               When the option --enable-gui=... is omitted,
               the default is the same of --enable-gui=kde,gtk
               To be able to build the kde gui,
               install the KDE development environment from [http://kde.org](http://kde.org)
               or .deb users: apt-get install kdelibs-dev
               or .rpm users: yum install <something-else>.
        JPEG flags are: default include path
        JPEG libs are: -ljpeg
        WARNING: No PNG library development package installed!
                 Gnash will be built without support for dynamic loading of PNG files.
                 Install it from [http://www.libpng.org](http://www.libpng.org)
                 or .deb users: apt-get install libpng12-dev
                 or .rpm users: yum install libpng-devel
        ERROR: GST media handling requested but gstreamer-0.10+ not found
               Install it from [http://www.gstreamer.net](http://www.gstreamer.net)
               or .deb users: apt-get install libgstreamer0.10-dev
               or .rpm users: yum install gstreamer-devel
        POSIX Threads flags are: -pthread
        POSIX Threads lib is: -lpthread
        WARNING: CURL library not found.
                 Gnash will be built without support for streaming from URLs.
                 Why not install libcurl from [http://curl.haxx.se/libcurl](http://curl.haxx.se/libcurl)
                 or .deb users: apt-get install libcurl3-dev
                 or .rpm users: yum install curl-devel
        AGG Pixel format is: all
        ERROR: No AGG development package installed!
               Install it from [http://www.antigrain.com](http://www.antigrain.com)
               or .deb users: apt-get install libagg-dev
               or .rpm users: yum install agg-devel
        ERROR: No BOOST development package installed!
               Install it from [http://www.boost.org](http://www.boost.org)
               or .deb users: apt-get install libboost-dev libboost-thread-dev
               or .rpm users: yum install boost-devel
        WARNING: You need to have the Ming development and utilities packages
                 installed to run most of the tests in Gnash testsuite.
                 Install it from [http://ming.sourceforge.net](http://ming.sourceforge.net)
                 or .deb users: apt-get install libming-dev
        WARNING: You need to have the MTASC compiler packages installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://mtasc.org](http://mtasc.org)
                 or .deb users: apt-get install mtasc
        WARNING: You need to have the 'swfmill' tool installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://swfmill.org/](http://swfmill.org/)
        WARNING: You need to have 'swfc' from SWFTools installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://www.swftools.org/](http://www.swftools.org/)
        PYTHON is /usr/bin/python
        WARNING: You need to have the zlib development packages installed
                 to play compressed SWF (most of them from version 6 up)
                 and to display some kinds of JPEG files.
                 Install it from [http://www.zlib.net](http://www.zlib.net)
                 or .deb users: apt-get install zlib1g-dev
                 or .rpm users: yum install zlib-dev.
                 It may still be possible to configure without zlib.
        WARNING: You need to have the freetype development packages installed
                 to use device fonts.
                 Install it from [http://www.freetype.org](http://www.freetype.org)
                 or .deb users: apt-get install libfreetype6-dev
                 or .rpm users: yum install libfreetype6-dev (??)
                 It may still be possible to configure without freetype.
        WARNING: You need to have the freetype development packages installed
                 to use device fonts.
                 Install it from [http://www.fontconfig.org](http://www.fontconfig.org)
                 or .deb users: apt-get install libfontconfig1-dev
                 or .rpm users: yum install ??
                 It may still be possible to configure without fontconfig.

configure: error: Please install required packages
shawngadwa@atlantis:~/Desktop/gnash-0.8.2$        

Its a mouthful...what now?

---

### Post by avtolle on 2008-04-29
What repositories do you have enabled? I've enabled all (under the third-party tab) except those related to source code. After I did this, I did a reload under Synaptic, and gnash; gnash-common; and the mozilla plugin were all there. Selected all for installation, installed. HTH.

---

### Post by shgadwa on 2008-04-29
ok....What is a repositories and where is the third party tab????

I tried to do waht you said with java and I get this...

[email]shawngadwa@atlantis:~/.mozi[/email]lla/plugins$ ln -s /usr/lib/j2sdk1.6-ibm/jre/plugin/ppc/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so' to `/usr/lib/j2sdk1.6-ibm/jre/plugin/ppc/ns7/libjavaplugin_oji.so': File exists
[email]shawngadwa@atlantis:~/.mozi[/email]lla/plugins$


I did it while firefox was off and then I opened firefox and java still does not work. I also have fastjar installed too and a lot of other java extentions or whatever.

---

### Post by avtolle on 2008-04-29
I would point you to this: [https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64)

and suggest you look under the part which discusses installation of java under ppc. What I think is happening is that you have multiple instances of Java installed, and the system doesn't know which one you want to use. So, check the version that is installed, ```
 java-version
``` and configure to the version you want to use, ```
sudo upadte-alternatives --config java
``` all as is contained in the Wiki article.

---

### Post by shgadwa on 2008-04-29
Thank you!

I typed in java-version in ther terminal and it said command not found. I do think that I have more than one java install isntalled...I also have fastjar and a lot of java extentions or whatever you want to call them..essentials. 

Soooo, when looking at the long lsit of stuff that it has when i search for "java"...which one do i select?? Jsut the java one or do I need others??

I will read that link.

---

### Post by avtolle on 2008-04-29
My typo. Should be ```
java -version
```.
You should select which version of java you wish to run. I cannot recall exactly the selections that appeared when I used the command ```
sudo update-alternatives --config java
```, but I selected the IBM Java as it performs the best for me. Hope this helps you.

---

