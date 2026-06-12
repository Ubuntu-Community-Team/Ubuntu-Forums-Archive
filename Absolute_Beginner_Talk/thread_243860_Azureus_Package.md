---
title: "Azureus Package"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by kiplingw on 2006-08-25
Does anyone know where I might find a package for Azureus 2.5.0.0 for Dapper? If not, are there instructions on how to build the package from the archive?

--
Kip Warner
Vertigo
[http://TheVertigo.com](http://TheVertigo.com)

---

### Post by Woei on 2006-08-25
> **kiplingw said:**
> Does anyone know where I might find a package for Azureus 2.5.0.0 for Dapper? If not, are there instructions on how to build the package from the archive?


Stable binary distributions like Ubuntu don't generally update software after a distribution version is released, unless it's absolutely necessary for security reasons. So either you'll have to wait for the next version of Ubuntu (Edgy Eft), or install the package yourself, removing the old package first.

Azureus is a bit of a cornercase, as it has built-in auto-updating facilities (which will not work with the version installed by Ubuntu), and it is using GNU Classpath instead of a regular JRE from Sun or IBM. To get optimum performance with Azureus, you'll probably have to download the Sun JRE as described more fully [here](https://jdk-distros.dev.java.net/ubuntu.html).    Then download the [tar archive](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download) off of one of SourceForge's mirrors. Extract with something like 'tar xjf Azureus_2.5.0.0_linux.tar.b2' in a terminal in the directory where you downloaded the archive (e.g.: your home directory itself). Then go into the new azureus directory. 'gedit azureus'. At the top of that file, enter /usr/lib/jvm/java-1.5.0-sun/jre between the empty "" after JAVA_PROGRAM_DIR.

Invoke azureus by pressing ALT+F2, 'azureus/azureus'. From now on, auto-updates initiated by Azureus itself will install in the azureus folder in your home directory.

---

### Post by Bachstelze on 2006-08-25
You could also look [here](https://wiki.ubuntu.com/AzureusHowTo), worked like a charm for me.

---

### Post by Perfect Storm on 2006-08-25
You could try this way: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

### Post by PaganHippie on 2006-08-26
Would this also require first uninstalling the Ubuntu-repo version?

---

### Post by Perfect Storm on 2006-08-26
Aye, will be a good idea.

---

### Post by Bachstelze on 2006-08-26
For me it worked fine jusr downloading the JAR from Azureus webite and copy/pasting it instead ot the ne that come with the Ubuntu package.

---

### Post by PaganHippie on 2006-08-26
I've considered that, but wasn't sure about dependencies; also, wouldn't you have to rename the .jar file?

---

### Post by Bachstelze on 2006-08-26
Yes of course, so that when you launch Azureus, it uses the new JAR instead of the old one. The link I posted explains it all.

---

### Post by atomikpunx on 2006-09-02
[http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

> 

wget [http://kent.dl.sourceforge.net/sourceforge/azureus/Azureus_2.5.0.0_linux.tar.bz2](http://kent.dl.sourceforge.net/sourceforge/azureus/Azureus_2.5.0.0_linux.tar.bz2)

sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2 -C /opt/

sudo gedit /usr/share/applications/azureus.desktop



on the link the 2nd line misspells azureus, so copy and paste mine.
simply uninstall 2.4.0.2 and install 2.5.0.0 in a command prompt, afterwards autoupdate will work fine.

---

