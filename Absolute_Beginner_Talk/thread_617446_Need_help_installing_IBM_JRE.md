---
title: "Need help installing IBM JRE"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by TalioGladius on 2007-11-19
So my ultimate goal is to run the Linux Groupwise client, which is heavily dependent on java from what I can tell.  I have it installed and it works.  However, it does not work with compiz, beryl, or any other eye-candy.  This is something that's difficult for me to give up.

So....I read that the problem is with Sun's java, which I am using, but it works perfectly with IBM's java runtime environment.  I downloaded the IBM JRE from here [http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

I went with the J2SE 1.4.2 SR9 for 32 bit x series.  I've got a folder with docs and jre directories underneath it and a ton of files/directories in them but no install .pl or makeinstall files from what I can see.  I think this is source code that needs to be compiled.

Anyone have a clue as to how I would install this?

---

### Post by TalioGladius on 2007-11-19
bump

---

### Post by Vadi on 2007-11-19
Are there any "README" files anywhere?

---

### Post by TalioGladius on 2007-11-19
There's a starthere.htm file in the docs folder.  For installation it only mentions redhat and these are the procedures....

> Installing on Red Hat Enterprise Linux (RHEL) |4 or 5|
|

For RHEL 4 and 5, the SDK depends on shared libraries that are not installed |by default.
|

In RHEL 4, the RPMs that contain these libraries are:
|

    * |compat-libstdc++-33-3.2.3 and xorg-x11-deprecated-libs-6.8.1 (Platforms other than zSeries)
    * |compat-libstdc++-295-2.95.3 and xorg-x11-deprecated-libs-6.8.1 (zSeries)
    * |

|

To include these libraries during RHEL 4 installation:
|

   1. |When you reach the Package Defaults screen, select Customize the set of packages to be installed.
   2. |At the Package Group Selection screen, under X Windows System, choose Details and |make sure that you have selected xorg-x11-deprecated-libs.
   3. |Under the Development options, select Legacy Software Development.

|

In RHEL 5, the RPMs that contain these libraries are:
|

    * ||libXp-1.0.0-8 (All platforms)|
    * |compat-libstdc++-33-3.2.3 (Platforms other than zSeries)
    * |compat-libstdc++-296-2.95.3 (zSeries)

|

|To include these libraries during RHEL 5 installation:|
|

   1. | |At the software selection screen, select Customize now.
   2. |On the next screen, in the left-hand panel, select Base System; in the right-hand panel, select Legacy Software Support. These selections will install the compat-libstdc++ |packages.
   3. |The libXp package is required but is not available to select for installation |from the install GUI. When installation is complete, open a shell, locate |the libXp package on your Red Hat installation media, and install it. For |example, to install on a 32-bit Intel platform: |

      rpm -i /media/cdrom/Server/libXp-1.0.0-8.i386.rpm

---

### Post by Vadi on 2007-11-19
Dunno.

Email IBM support?

---

### Post by erm4gh on 2007-11-19
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) has instructions for installing IBM's Java implementation, among others.

---

### Post by TalioGladius on 2007-11-19
> **erm4gh said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) has instructions for installing IBM's Java implementation, among others.It only mentions installing the IBM java on powerPCs.  I tried switching to the free java, but didn't work.  Complained about lack of 
version information.

---

