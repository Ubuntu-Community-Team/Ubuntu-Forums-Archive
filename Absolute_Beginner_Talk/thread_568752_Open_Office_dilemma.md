---
title: "Open Office dilemma"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-10-06
Ok, there was an update to my Open Office installation that I installed using ubuntu's updater.
I had not been able to use the Open Office DB program previously - it would hand during the last stages of form design.

So, I eagerly anticipated the installation of this update hoping that it would solve my problems.

Unfortunately, following the update, I cannot open OODB.  It complains about my verion of Java.

I have purposely downgraded my Java from the latest version because Logmein that I use to access my office computer from my home will not function with the latest version of java.  I believe the latest version of java for Ubuntu is version 6, I'm running version 5.

Can anyone offer some suggestions?

Thanks.

Caruso

---

### Post by Maxtorm on 2007-10-06
Different versions of the Java Runtime Environment can co-exist. You can install the new version of the Java Runtime Environment and then point OO.o to the new version using Tools -> Options -> OpenOffice.org -> Java.

---

### Post by swisscow on 2007-10-06
I have found that removing the ubuntu version of openoffice and downloading and installing the version from the open office web site also solves these sort of problems.

---

### Post by carusoswi on 2007-10-13
> **swisscow said:**
> I have found that removing the ubuntu version of openoffice and downloading and installing the version from the open office web site also solves these sort of problems.

Ok, I removed OO from my Ubuntu machine.  Went to the website to download their version.  Can't figure it out.  Something about bit torrents, RMS, etc.

Can you walk me through the process?

I would appreciate it.  Usually, I just download the package and Ubuntu takes it from there.

Thanks.

Caruso

---

### Post by vanadium on 2007-10-13
The procedure to install OOo from the OOo website involves downloading the installation archive. You need to uncompress it and a foldere containing *.rps (redhat installation files) will result. These need to be converted to *.deb installation packages, that then can be installed using dpkg. This is the principle, and if you do an internet search, you should find detailled instructions of this (probably this can be found on [www.openoffice.org](www.openoffice.org) anyway).

I would be more inclined to follow Maxstorms' suggestion on jave, though.

---

### Post by vanadium on 2007-10-13
By coincidence, I found the commands three threads below:

[http://ubuntuforums.org/showthread.php?t=552499](http://ubuntuforums.org/showthread.php?t=552499)

---

