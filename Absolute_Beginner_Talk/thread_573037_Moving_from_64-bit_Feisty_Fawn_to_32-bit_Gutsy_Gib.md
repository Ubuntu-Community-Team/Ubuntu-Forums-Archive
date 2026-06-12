---
title: "Moving from 64-bit Feisty Fawn to 32-bit Gutsy Gibbon"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by leefw on 2007-10-11
Hi

I have come to the conclusion that buying 64-bit hardware was a big mistake! Today I am using a 64 bit version of Kubuntu Feisty Fawn. Since Gutsy Gibbon is right around the corner I was considering just replacing the 64-bit version of Feisty with the 32-bit version of Gutsy. 

I want to keep all of my data (images, video, music, Amarok configuration, other files etc). Today the machine has 4 hard drives. The Linux distribution itself is only on one (images, video, music are the others). Amarok uses MySQL for configuration etc. 

What is the easiest way to go about doing this? Delete the partitiion or install right over it? My understanding is that only compiled program code will be affected so I will have to install all the distribution applications again. I can live with that...

But I do not want to lose my Amarok configuration. Is it correct to assume that a MySQL database on 64-bit MySQL will be the same on the 32-bit architecture? 

Also, the actual filesystem (ext3) itself is not affected. Correct?

Any help you can offer will be much appreciated...

Regards
Lee Francis

---

### Post by leefw on 2007-10-11
FYI: This [thread]("http://ubuntuforums.org/showthread.php?t=573071") touches the same topic

---

### Post by hyper_ch on 2007-10-11
64bit on Gutsy is a lot more advanced than on Feisty (as I read from various threads here)... so you could maybe first try the 64bit Gutsy version before totally dropping it right now.

---

### Post by mivo on 2007-10-11
Why do you feel that buying 64-bit hardware was a big mistake? There are issues in Feisty, true, but as was said, support is much better in Gutsy. In time, I think all that will be sold will be 64-bit, so going back now is only a temporary measure. I'd stick with it, unless you still have troubles in Gutsy.

---

### Post by dptxp on 2007-10-11
> **leefw said:**
> Hi

I have come to the conclusion that buying 64-bit hardware was a big mistake! 

Lee Francis

You get only 64 bit hardware now (CPU), they are backward compatible with 32-bit OS.
They run both 32-bit and 64-bit, so what is wrong with 64-bit hardware ?

---

### Post by leefw on 2007-10-11
I guess I'm not really saying there is a problem with 64-bit hardware, but drivers etc is a problem. I am also missing flash for Firefox, Wine won't work etc. I guess it's the 64-bit OS that's the problem, not the actual hardware.

---

### Post by mivo on 2007-10-11
Flash in Firefox works in 64-Bit Gutsy. As for Wine, see [here]("http://wiki.winehq.org/WineOn64bit"). :)

---

### Post by funrider on 2007-10-11
you can export your db to a flat file. after the migration do an import from the 32 bit machine.

we will see if ff on gg64 works well. anyway konqueror can work with flash in gg so i guess it doesnt matter now.

---

### Post by dptxp on 2007-10-11
> **leefw said:**
> I guess I'm not really saying there is a problem with 64-bit hardware, but drivers etc is a problem. I am also missing flash for Firefox, Wine won't work etc. I guess it's the 64-bit OS that's the problem, not the actual hardware.

Whenever you have a problem specific to 64 bit, post in 64-bit forum here,
you will find simple solutions.

---

### Post by leefw on 2007-10-12
> **hyper_ch said:**
> 64bit on Gutsy is a lot more advanced than on Feisty (as I read from various threads here)... so you could maybe first try the 64bit Gutsy version before totally dropping it right now.
OK, I guess that is the best starting point. Thanks!

---

### Post by leefw on 2007-10-15
> **dptxp said:**
> They run both 32-bit and 64-bit, so what is wrong with 64-bit hardware ?
This is what I'm talking about... 

I want to install VMware server... just browsed through the [release notes]("http://www.vmware.com/support/server/doc/releasenotes_server.html"):

 ```


Support for 32-bit and 64-bit Operating Systems
    * Full support for SUSE Linux 10.1 as host and guest operating systems.
    * Full support for 32-bit Ubuntu 6.x as host and guest operating systems.
    * Full support for 32-bit Sun Solaris 10.x as guest operating systems.
    * Full support for 32-bit and 64-bit FreeBSD 6.0 as guest operating systems.
    * Experimental support for Red Hat Enterprise Linux 3.0 Update 8 and Red Hat Enterprise Linux 4.0 Update 4.
    * Experimental support for 64-bit Ubuntu 6.x as host and guest operating systems.
    * Experimental support for 64-bit Sun Solaris 10.x as guest operating systems.
    * Support for all guest operating systems supported by Workstation 5.5.
    * Support for all host operating systems supported by VMware Server GSX 3.2. 
```

This applies to version 1.0 (but doesn't seem to have been updated since, so I am assuming it still applies)...

No, I know it's not the fault of the actual 64-bit OS, but it just seems to me that 64-bit software isn't quite "there" yet.

---

### Post by dptxp on 2007-10-15
> **leefw said:**
> This is what I'm talking about... 

I want to install VMware server... just browsed through the [release notes]("http://www.vmware.com/support/server/doc/releasenotes_server.html"):

 ```


Support for 32-bit and 64-bit Operating Systems
    * Full support for SUSE Linux 10.1 as host and guest operating systems.
    * Full support for 32-bit Ubuntu 6.x as host and guest operating systems.
    * Full support for 32-bit Sun Solaris 10.x as guest operating systems.
    * Full support for 32-bit and 64-bit FreeBSD 6.0 as guest operating systems.
    * Experimental support for Red Hat Enterprise Linux 3.0 Update 8 and Red Hat Enterprise Linux 4.0 Update 4.
    * Experimental support for 64-bit Ubuntu 6.x as host and guest operating systems.
    * Experimental support for 64-bit Sun Solaris 10.x as guest operating systems.
    * Support for all guest operating systems supported by Workstation 5.5.
    * Support for all host operating systems supported by VMware Server GSX 3.2. 
```

This applies to version 1.0 (but doesn't seem to have been updated since, so I am assuming it still applies)...

No, I know it's not the fault of the actual 64-bit OS, but it just seems to me that 64-bit software isn't quite "there" yet.

OP said that buying 64-bit hardware was a mistake, you can run 32 bit software with
equal ease on 64 bit hardware, fully compatible.

---

