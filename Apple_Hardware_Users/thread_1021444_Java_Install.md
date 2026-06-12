---
title: "Java Install?"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by greenbjb on 2008-12-25
Just installed latest ubuntu 8.10 on G4 PowerPC Mac.  Starting to work my way through the various things that are not working.  Java, sound, etc.  Can someone point me to the documentation, forums, etc.  that have info on this.  I'm a newb to ubuntu. 

thanks. 

Jim G.

---

### Post by jamesstansell on 2008-12-25
> **greenbjb said:**
> Just installed latest ubuntu 8.10 on G4 PowerPC Mac.  Starting to work my way through the various things that are not working.  Java, sound, etc.  Can someone point me to the documentation, forums, etc.  that have info on this.  I'm a newb to ubuntu. 

thanks. 

Jim G.

A typical way to install java is by using the ubuntu-restricted-extras package.

Or, more directly, you might use openjdk-6-jre and/or icedtea6-plugin.

Sorry, not speaking from direct experience, since I don't have powerpc.  I'm not positive if these packages are available to you.

---

### Post by namdung on 2008-12-25
> **greenbjb said:**
> Just installed latest ubuntu 8.10 on G4 PowerPC Mac.  Starting to work my way through the various things that are not working.  Java, sound, etc.  Can someone point me to the documentation, forums, etc.  that have info on this.  I'm a newb to ubuntu. 

thanks. 

Jim G.

Use the *System-->Admin-->Synaptic package Manager* to install Java (Recommended sun-jre)

Go to *System-->Preferences-->Sound* to configure sound options. Most times the *autodetect* option serves well.

These issues has been discussed several times in this forum. Pls use the *Search* option. 

Pls mention specific issue for further help.

---

### Post by greenbjb on 2008-12-25
Thanks but I've already tried searching the forum.. no luck.  Tried your tips.. no luck either.  I appreciate you trying.

---

### Post by tiresia on 2008-12-25
You can install Java 6 for PowerPC downloading it from IBM (you need to register). It worked for me, when I did it.
Do not forget you have a powerpc32 (not 64 bit)
[http://www.ibm.com/developerworks/systems/library/es-apple.html](http://www.ibm.com/developerworks/systems/library/es-apple.html)
This is a guide to install it
[http://www.debianhelp.co.uk/debianjava.htm](http://www.debianhelp.co.uk/debianjava.htm)

---

### Post by mkvnmtr on 2008-12-26
In the medibuntu there are two java programs from IBM.. I had never had any luck with the restricted extras so the last time I reinstalled I used one of them. It works for me. I assume it is the same as you download from IBM.

---

### Post by greenbjb on 2009-01-01
> **tiresia said:**
> You can install Java 6 for PowerPC downloading it from IBM (you need to register). It worked for me, when I did it.
Do not forget you have a powerpc32 (not 64 bit)
[http://www.ibm.com/developerworks/systems/library/es-apple.html](http://www.ibm.com/developerworks/systems/library/es-apple.html)
This is a guide to install it
[http://www.debianhelp.co.uk/debianjava.htm](http://www.debianhelp.co.uk/debianjava.htm)

Thanks for these links, I maybe almost there.  Following the first link to the IBM java site has good instructions but I don't see any obvious link for the PowerPC32 version of Java 6. If you follow that link you get a bunch of versions none of which seem to be the right one. The install link that takes you to the Debian site has a different link to the IBM java versions to download.  At that site ([http://www-128.ibm.com/developerworks/java/jdk/linux/download.html](http://www-128.ibm.com/developerworks/java/jdk/linux/download.html)) it also isn't clear which version to download.  The various terminologies make it difficult. Is it the 32bit iSeries/PSeries version?

---

### Post by linux_tech on 2009-01-01
The 32-bit iSeries/pSeries would be the correct one.

---

### Post by mkvnmtr on 2009-01-01
There is no need to down load from IBM. It is in the package manager Synaptic after you enable medibuntu  repository. There are a lot of other things you will probably want the also. Like codexs so you can play nearly everything. One of the tutiorals can explain better than me how to enable medibuntu. Google it and you will get several in the Ubuntu wiki

---

