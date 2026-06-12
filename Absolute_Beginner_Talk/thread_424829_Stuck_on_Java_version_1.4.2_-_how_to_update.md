---
title: "Stuck on Java version 1.4.2 - how to update?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by stevenrushing on 2007-04-27
This is my output:

    steven@steven-desktop:~$ java -version
    java version "1.4.2"
    gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

    Copyright (C) 2006 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions. There is NO
    warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
    steven@steven-desktop:~$ 

But when i try to apt-get the new one, it says I have the most recent version.

Any ideas? =)

Steven Rushing

---

### Post by crav on 2007-04-27
If you've already got Java 1.5 or 1.6 you'll need to do this to switch virtual machines:
```
sudo update-alternatives --config java
```

---

### Post by stevenrushing on 2007-04-27
Thank you for your quick response!  =)

ubuntu@ubuntu:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.
ubuntu@ubuntu:~$

---

### Post by YoG%*@ on 2007-04-27
> **stevenrushing said:**
> This is my output:

But when i try to apt-get the new one, it says I have the most recent version.

Steven Rushing

which command did you use to apt-get the new java package?

---

### Post by stevenrushing on 2007-04-27
I actually pulled a stupid.  =)  I downloaded the player from [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

using the self extracting file (option 2)

I am really new to ubuntu (old linspire user)

Steven Rushing

---

### Post by YoG%*@ on 2007-04-27
so, what about giving 
```

sudo aptitude install sun-java5-jdk

```
a try? =)

hth

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ sudo aptitude install sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-jdk"
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils ekiga evince evolution 
  evolution-plugins file firefox firefox-gnome-support gdm gnupg info 
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3 libdns21 
  libfreetype6 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 libpoppler1 libpoppler1-glib libsmbclient 
  libsoup2.2-8 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno samba-common screen 
  slocate smbclient tar tcpdump ttf-opensymbol w3m xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
ubuntu@ubuntu:~$

---

### Post by YoG%*@ on 2007-04-27
oh, i forgot, the sun-java packages are in the multiverse repos. 
you have to add them to your /etc/apt/sources.list
can you try that?

---

### Post by stevenrushing on 2007-04-27
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I did a google search to see what you were talking about and came up with that... i folowed the directions.  does that do the same as this /etc/apt/sources.list?

also, will run that same command you directed before after the repositories are added unless you tell me not to.  =)

---

### Post by YoG%*@ on 2007-04-27
> **stevenrushing said:**
> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I did a google search to see what you were talking about and came up with that... i folowed the directions.  does that do the same as this /etc/apt/sources.list?

also, will run that same command you directed before after the repositories are added unless you tell me not to.  =)

yes, that's what i meant! just the graphical way to do it =)
now run 
```

sudo aptitude update

```
and then 
```

sudo aptitude install sun-java5-jdk

```

let me know, if it worked!

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ sudo aptitude install sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following NEW packages will be automatically installed:
  gsfonts-x11 java-common libltdl3 odbcinst1debian1 sun-java5-bin 
  sun-java5-demo sun-java5-jre unixodbc 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils ekiga evince evolution 
  evolution-plugins file firefox firefox-gnome-support gdm gnupg info 
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3 libdns21 
  libfreetype6 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 libpoppler1 libpoppler1-glib libsmbclient 
  libsoup2.2-8 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno rdesktop samba-common 
  screen slocate smbclient tar tcpdump ttf-opensymbol w3m xserver-xorg-core 
The following NEW packages will be installed:
  gsfonts-x11 java-common libltdl3 odbcinst1debian1 sun-java5-bin 
  sun-java5-demo sun-java5-jdk sun-java5-jre unixodbc 
0 packages upgraded, 9 newly installed, 0 to remove and 101 not upgraded.
Need to get 45.3MB of archives. After unpacking 117MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  sun-java5-bin sun-java5-jdk sun-java5-jre java-common unixodbc 
  odbcinst1debian1 sun-java5-demo libltdl3 gsfonts-x11 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": y
Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main java-common 0.25ubuntu1 [76.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libltdl3 1.5.22-4 [168kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main unixodbc 2.2.11-13 [269kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-bin 1.5.0-08-0ubuntu1 [22.3MB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-jre 1.5.0-08-0ubuntu1 [7454kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-demo 1.5.0-08-0ubuntu1 [9889kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-jdk 1.5.0-08-0ubuntu1 [5036kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main gsfonts-x11 0.20build1 [10.6kB]       
Fetched 45.3MB in 4m47s (158kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 102187 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu1_all.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-13_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-13_i386.deb) ...
Selecting previously deselected package sun-java5-bin.
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb) ...
Selecting previously deselected package sun-java5-jre.
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java5-demo.
Unpacking sun-java5-demo (from .../sun-java5-demo_1.5.0-08-0ubuntu1_i386.deb) ...
Selecting previously deselected package sun-java5-jdk.
Unpacking sun-java5-jdk (from .../sun-java5-jdk_1.5.0-08-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Setting up java-common (0.25ubuntu1) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Setting up sun-java5-jre (1.5.0-08-0ubuntu1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 27f8
Wrote aliases at 27f8 - 29ac
Wrote parents at 29ac - 337c
Wrote literal globs at 337c - 33e0
Wrote suffix globs at 33e0 - 6778
Wrote full globs at 6778 - 679c
Wrote magic at 679c - bdac
Wrote namespace list at bdac - bdbc
***

Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sun-java5-jdk (1.5.0-08-0ubuntu1) ...

Setting up sun-java5-demo (1.5.0-08-0ubuntu1) ...

Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
ubuntu@ubuntu:~$

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by YoG%*@ on 2007-04-27
hm... not sure about the error.
can you select the new java version and then check with java -version? 
also, try [http://ubuntuguide.org/wiki]("http://ubuntuguide.org/wiki") - they have a section about installing java and the like.

---

### Post by stevenrushing on 2007-04-27
thank you for your help.  I appreciate it.  Will check out the wiki

ubuntu@ubuntu:~$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

---

### Post by YoG%*@ on 2007-04-27
forgot to ask: which version of ubuntu are you running? 
if you've feisty installed, maybe you should go for java6?

---

### Post by stevenrushing on 2007-04-27
6.10  I think that is edgy?...smr

---

### Post by stevenrushing on 2007-04-27
I wish there were an easy way to "start over".  I need a do over!  =) So I would do it right the first time, instead of downloading and trying to install it that way.  Is there a way to uninstall what i have already done?

---

### Post by YoG%*@ on 2007-04-27
```

sudo aptitude remove sun-java5-jdk

```
should remove what's been installed before

---

### Post by stevenrushing on 2007-04-27
this is hilarious!  =)  it tried, but couldn't uninstall it.  

ubuntu@ubuntu:~$ sudo aptitude remove sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  sun-java5-demo 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils ekiga evince evolution 
  evolution-plugins file firefox firefox-gnome-support gdm gnupg info 
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3 libdns21 
  libfreetype6 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 libpoppler1 libpoppler1-glib libsmbclient 
  libsoup2.2-8 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno rdesktop samba-common 
  screen slocate smbclient tar tcpdump ttf-opensymbol w3m xserver-xorg-core 
The following packages will be REMOVED:
  sun-java5-jdk 
0 packages upgraded, 0 newly installed, 2 to remove and 101 not upgraded.
Need to get 0B of archives. After unpacking 32.1MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 105113 files and directories currently installed.)
Removing sun-java5-jdk ...
Removing sun-java5-demo ...
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
ubuntu@ubuntu:~$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
ubuntu@ubuntu:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by YoG%*@ on 2007-04-27
hehe... omg, didn't think this would be so tricky =)
can you do a 
```

locate libjava.so

```
?

---

### Post by stevenrushing on 2007-04-27
Tricky?  It is downright impossible!  At least you know what all these outputs mean.  (although I am learning alot.  =)

ubuntu@ubuntu:~$ locate libjava.so
locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
ubuntu@ubuntu:~$

---

### Post by YoG%*@ on 2007-04-27
try 
```

sudo updatedb
locate libjava.so

```

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ locate libjava.so
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjava.so

---

### Post by YoG%*@ on 2007-04-27
that's the place it should be... 
can you post the output of 
```

export | grep java

``` ?

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ export | grep java
ubuntu@ubuntu:~$

---

### Post by YoG%*@ on 2007-04-27
please try to set 
```

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

```
in a terminal and then try to remove/install again

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
ubuntu@ubuntu:~$ sudo aptitude remove sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils ekiga evince evolution 
  evolution-plugins file firefox firefox-gnome-support gdm gnupg info 
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3 libdns21 
  libfreetype6 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 libpoppler1 libpoppler1-glib libsmbclient 
  libsoup2.2-8 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno rdesktop samba-common 
  screen slocate smbclient tar tcpdump ttf-opensymbol w3m xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 101 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin

---

### Post by YoG%*@ on 2007-04-27
sorry, my mistake, didn't read properly: 
> **mux said:**
> please try to set 
```

export JAVA_HOME=/usr/lib/jvm/java-1.5.0

```
in a terminal and then try to remove/install again

please try it one more time =)
```

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-1.5.0.08

```

---

### Post by stevenrushing on 2007-04-27
ubuntu@ubuntu:~$ export JAVA_HOME=/usr/lib/jvm/java-1.5.0-1.5.0.08
ubuntu@ubuntu:~$ sudo aptitude remove sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils ekiga evince evolution 
  evolution-plugins file firefox firefox-gnome-support gdm gnupg info 
  libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3 libdns21 
  libfreetype6 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1 
  libkrb53 liblwres9 libmagic1 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpng12-0 libpoppler1 libpoppler1-glib libsmbclient 
  libsoup2.2-8 libwpd8c2a libx11-6 libx11-data libxfont1 linux-generic 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic 
  linux-headers-generic mono-common mono-gac mono-jit mono-runtime 
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno rdesktop samba-common 
  screen slocate smbclient tar tcpdump ttf-opensymbol w3m xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 101 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-bin
ubuntu@ubuntu:~$

---

### Post by YoG%*@ on 2007-04-27
i'm very sorry, but i'm seriously running out of ideas... 
maybe you can try a manual install: [http://blog.webhosting.uk.com/2006/10/25/installing-jdk-in-debian/]("http://blog.webhosting.uk.com/2006/10/25/installing-jdk-in-debian/")
?

---

### Post by stevenrushing on 2007-04-27
You have been more help and been here more hours than I could've possibly expected from well paid techs.  Thank you very very much.  =)

---

### Post by YoG%*@ on 2007-04-27
you're welcome =)

hope you'll find a solution to your problem!

---

### Post by matevz on 2007-05-02
Hi.  I'm kind of late to the party, but I recently install java5 and I noticed some differences in how you went about it.
First of all (and this may be revealing my ignorance here), is there a difference between using aptitude and apt-get?
Also, make sure your /etc/apt/sources.list file is pointing to the correct repositories:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse 

if you need to change those, afterward run the command: sudo apt-get update

Then, try this command:

sudo apt-get install sun-java5-jdk

I don't know if this is going to make any difference, but it worked for me.

Good luck,
Matt

---

### Post by Dogmeat Jack on 2007-09-07
Found the answer:
[http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412]("http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412")
basicly run :
```
sudo update-alternatives --config java
```
and select your preferred Java version

---

### Post by kruppe on 2007-09-08
Thank you, this worked first time. :)

> **mux said:**
> so, what about giving 
```

sudo aptitude install sun-java5-jdk

```a try? =)

hth

---

