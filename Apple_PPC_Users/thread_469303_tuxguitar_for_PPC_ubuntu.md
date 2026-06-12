---
title: "tuxguitar for PPC ubuntu?"
date: 2007-06-09
forum: Apple PPC Users
---

### Post by [censored] on 2007-06-09
Anyone ever got tuxguitar to work on PPC ubuntu? 

[http://www.tuxguitar.com.ar/tgwiki/doku.php](http://www.tuxguitar.com.ar/tgwiki/doku.php)

Been trying, but I keep getting java errors trying to run it.

Any help would be appreciated. ta.

---

### Post by Auria on 2007-06-09
what exactly have you been trying?

It's Java - Sun's Java is not available - so we'll need to know if IBM's VM can handle that. (GCJ is know to not work) you'll first need to install the IBM vm

Then we need SWT for linux PPC ([http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/index.php#swt](http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/index.php#swt))
It is noted to be compatible with SUSE and RedHat so there might be problems installing on Ubuntu. It might be needed to install from source.

then we'd need to build tg from source ([http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:build](http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:build))

---

### Post by [censored] on 2007-06-09
Hi Aura. Have pretty much followed the steps above, with a couple of differences:

1) I installed ibm java from the medibuntu repositories.

ii  ibm-j2sdk1.5      1.5.0-0medibuntu1    Java(TM) JDK, Standard Edition, IBM Corporat

2) I installed swt from the ubuntu repos

ii  libswt3.1-gtk-java 3.1.2-3ubuntu1 Fast and rich GUI toolkit for Java, gtk2 ver
ii  libswt3.1-gtk-jni 3.1.2-3ubuntu1  Platform dependent files for libswt3.1-gtk-j

I followed the instructions on how to build from source on the tuxguitar site.  In the build.properties file, I simply commented out the "default linux build properties", and un-commented "ubuntu dapper build properties". Then I typed "ant" in the console.

At the end of the build process, I got a .deb file, which refuses to install because it says it's specific to i386.

In the install directory there is now a source directory, with an executable script called "tuxguitar". But if I try executing it, I just get a flood of java errors.

I've read all the instructions, but I'm not sure what I'm supposed to do here.

---

### Post by Auria on 2007-06-09
if the deb says it's i386 only it's maybe because the tuxguitar author never thought about PPC... best thing to do could be to contact him (or fix the ant files if you can of course ;) )

EDIT: we should also make sure the swt of the repos is compatible with IBM VM

---

### Post by luckyd on 2007-06-10
Have you tried compiling the source manually?

---

### Post by Auria on 2007-06-10
> **luckyd said:**
> Have you tried compiling the source manually?

> 

I followed the instructions on how to build from source on the tuxguitar site. In the build.properties file, I simply commented out the "default linux build properties", and un-commented "ubuntu dapper build properties". Then I typed "ant" in the console.

At the end of the build process, I got ...

:)

---

### Post by luckyd on 2007-06-10
my bad ;)

---

### Post by [censored] on 2007-06-11
Got it working. I just re compiled, using the DEFAULT LINUX option in the build.properties file.

It works. Only problem now is that the midi sounds like something truly from the bowels of Satan himself. I expect that's a problem with the jre I'm using. ibm-j2sdk1.5  1.5.0-0medibuntu1

Any other options?

---

### Post by luckyd on 2007-06-11
As far as java for powerpc goes, the ibm version is the best...

---

### Post by Auria on 2007-06-11
> **'[censored] said:**
> Got it working. I just re compiled, using the DEFAULT LINUX option in the build.properties file.

It works. Only problem now is that the midi sounds like something truly from the bowels of Satan himself. I expect that's a problem with the jre I'm using. ibm-j2sdk1.5  1.5.0-0medibuntu1

Any other options?

Sun's Java uses synthesizer somewhere... you,d need to search where the IBM VM stores the synthesizer and if there is a way to install a better one.

Another option is to install the tuxguitar alsa plugin ([http://tuxguitar.com.ar/download.html](http://tuxguitar.com.ar/download.html), near the bottom) and thus use alsa midi instead of java midi (you can then install timidity and whatever synthesizer you want, and run it in alsa deamon mode to enable midi playback in alsa)

---

### Post by [censored] on 2007-07-08
> **Auria said:**
> 
Another option is to install the tuxguitar alsa plugin ([http://tuxguitar.com.ar/download.html](http://tuxguitar.com.ar/download.html), near the bottom) and thus use alsa midi instead of java midi (you can then install timidity and whatever synthesizer you want, and run it in alsa deamon mode to enable midi playback in alsa)

Thanks Auria, but try as I might, I can't see an ALSA plugin there.

---

### Post by Auria on 2007-07-08
> **'[censored] said:**
> Thanks Auria, but try as I might, I can't see an ALSA plugin there.

err ???

> 
TuxGuitar Download Page
Latest Version 0.9.1

    * Source Files
    * Ubuntu Binary Package
    * Debian Binary Package
    * Linux-x86 Installer
    * Linux-x86 Binary Files
    * Linux-x86_64 Binary Files
    * Windows-x86 Installer
    * MacOS Files

[b]
TuxGuitar Alsa Plugin[/b] <------- HERE

    * Source Files
    * Ubuntu Binary Package
    * Linux-x86 Binary Files


Old Versions

Click here to download older versions of TuxGuitar


---

