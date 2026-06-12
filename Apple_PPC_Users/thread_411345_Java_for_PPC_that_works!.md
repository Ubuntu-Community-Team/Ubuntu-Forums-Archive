---
title: "Java for PPC that works!"
date: 2007-04-16
forum: Apple PPC Users
---

### Post by engla on 2007-04-16
I have finally found a way to install java properly on PPC. I found this on a blog today and have only tried out just one java application so far. But I have high hopes for this one, so help me check this out.

[Java on Linux/PPC]("http://peter.makholm.net/2007/04/16/java-on-linuxppc/")
> 
   1. Download IBM’s java-package from [http://www-128.ibm.com/developerworks/java/jdk/linux/download.html](http://www-128.ibm.com/developerworks/java/jdk/linux/download.html) (registration required) - you need the 32bit iSeries/pSeries version in tgz format
   2. Make sure that the package includes …/jre/bin/libjavaplugin_oji.so (somehow I got a package which didn’t have the file)
   3. install java-package
   4. run make-jpkg <tgz file>. If it complain about “no matching plugin was found” look in /usr/share/doc/java-package/SUPPORTED and rename you tgz file to something supporte of alomos the correct version.
   5. Install the resulting package and restart firefox (whatever it is named today)

I downloaded a file called ibm-java2-jre-5.0-4.0-linux-ppc.tgz and renamed it to ibm-java2-jre-50-linux-ppc.tgz and it seems to work.

Notes: 
It seems like you have to put in a password to get to the download. I looked up a user at bugmenot.com (for ibm.com)
Install the package 'java-package' with apt-get to get the make-jpgk tool

Now the application I wanted to get to work, the 
[Brettspielwelt Client]("http://ubuntuforums.org/showthread.php?p=2465182") finally works fine! This looks like a solid java runtime for ppc.

---

### Post by fkdev on 2007-04-17
I believe IBM's java is also in the medibuntu repositories (for those who dislike registration).
Note that this will not necessarily get the latest and greatest version.

see [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

EDIT: The package is ibm-j2re1.5, I believe. If you opt to use this method, you may still have to make the symlink for the 
browser plugin and use update-alternatives (see the wiki)

This is an ALTERNATIVE method to the wiki one. If you don't minding registering, you should probably use the wiki (direct from ibm)

---

### Post by SycloneMedia on 2007-04-17
> **fkdev said:**
> I believe IBM's java is also in the medibuntu repositories (for those who dislike registration).
Note that this will not necessarily get the latest and greatest version.

see [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Hey thanks for the info! I got Java working now and Frostwire starts up no problem...

I tried the orignal poster's installation first... it did everything, but it just didn't work. Then when I added the MediBuntu repo, the update manager automatically notified me that an update was available for that original java installation. It was the same file, but I guess it made whatever was wrong, right. Cool.

UPDATE: Java is not working correctly after all. Frostwire freezes. Java quits after. :(

---

### Post by badgerclan on 2007-04-18
If more users would check the Ubuntu Wiki and HOWTO's there wouldn't be so many false leads. What you are looking for is at: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

or if you really lazy I've got it compiled at:
 [ftp://ftp.eskimo.com/u/b/badger//downloads/Debian/MacMini-G4/ibm-j2sdk1.5_1.5.0_powerpc.deb](ftp://ftp.eskimo.com/u/b/badger//downloads/Debian/MacMini-G4/ibm-j2sdk1.5_1.5.0_powerpc.deb)

:popcorn: 
badgerclan

---

### Post by engla on 2007-04-18
> **badgerclan said:**
> If more users would check the Ubuntu Wiki and HOWTO's there wouldn't be so many false leads. What you are looking for is at: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

or if you really lazy I've got it compiled at:
 [ftp://ftp.eskimo.com/u/b/badger//downloads/Debian/MacMini-G4/ibm-j2sdk1.5_1.5.0_powerpc.deb](ftp://ftp.eskimo.com/u/b/badger//downloads/Debian/MacMini-G4/ibm-j2sdk1.5_1.5.0_powerpc.deb)

:popcorn: 
badgerclan
Thanks! Those instructions are though completely identical to the ones I linked to, with the difference of choosing the SDK instead of the RE. Do you know what the difference is?

---

### Post by Auria on 2007-04-18
> **engla said:**
> Thanks! Those instructions are though completely identical to the ones I linked to, with the difference of choosing the SDK instead of the RE. Do you know what the difference is?

AFAIK SDK will enable you to write Java apps, whereas RE will only let you run java apps

---

### Post by qrwe on 2007-04-26
This Java solutions (or should I say suggestions) should be promoted as regular packages for PPC users in the Ubuntu package collection! How do you suggest it to the developers?

---

