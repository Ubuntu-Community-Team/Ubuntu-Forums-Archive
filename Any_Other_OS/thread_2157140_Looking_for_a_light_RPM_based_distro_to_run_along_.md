---
title: "Looking for a light RPM based distro to run along side Ubuntu 13.04"
date: 2013-06-24
forum: Any Other OS
---

### Post by Derelinquat fenestras on 2013-06-24
Hello,

I'm looking for a light weight RPM based distro to run along side Ubuntu.  I've used Fedora before (version 16, I believe) and I liked the interface, however it ran pretty slow on my machine (dual core intel atom, but only 2GB RAM).

What I'm trying to achieve is have a separate OS that will run Cinepaint, with minimal other applications, and use Ubuntu for my remaining operations.  

Any suggestions/advice would be greatly appreciated

---

### Post by roywhite on 2013-06-24
You Can try PCLOS. Don't know if they have a current lightweight version or not but the regular version runs pretty fast on my old computer(amd4000 cpu).
You can always remove the apps you don't need. Don't know about cinepaint. Good luck in your search

---

### Post by ajgreeny on 2013-06-24
Why specifically an RPM distro, unless you simply fancy running one as an alternative to a deb distro.
EDIT:
OK, I've just seen your other post about deep-painting applications (not sure what you mean by that) nor do I have anything to say about cinepaint.

What about using the ubuntu mini.iso [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and then just adding whatever you need for a truly minimal distro, using openbox or similar as a WM; it can not get much smaller than that.

If it must be a RPM distro have a look also at CentOS, or do a search at [DistroWatch.com]("http://distrowatch.com/")

---

### Post by mips on 2013-06-24
> **Derelinquat fenestras said:**
> 
**What I'm trying to achieve is have a separate OS that will run Cinepaint**, with minimal other applications, and use Ubuntu for my remaining operations.  


Why?

---

### Post by snowpine on 2013-06-24
CentOS and Scientific are very nice for low-end hardware.

---

### Post by Derelinquat fenestras on 2013-06-25
Thank you all for your replies.

The reason I would like to find an RPM OS is I am interested in trying Cinepaint because I am a photojournalist/digital artist and cinepaint allows to to paint in 8, 16, 32 bit color space (whereas GIMP only allows for 8bit).  Cinepaint is no longer provides in deb repositories, and the PPAs that I've found that are supposed to carry it do not work (404 error).  It is, however, offered as an RPM package.  

I tried to convert it with alien, but does not function properly,  I have also tried to build it from the .tar.bz package from SourceForge... but I haven't been able to get it to run... worked on it for a while, but decided to investigate/research other options...  So I was just thinking if I had a small light weight distro on a small partition that I could test/run Cinepaint (or other RPM packages) and do the remained of my computing, editing, et cetera on the Ubuntu partition.

Sorry I didn't quite make all of that clear...

---

### Post by mips on 2013-06-25
> **Derelinquat fenestras said:**
> 
I tried to convert it with alien, but does not function properly,  I have also tried to build it from the .tar.bz package from SourceForge... but I haven't been able to get it to run... worked on it for a while, but decided to investigate/research other options...

Understood ;) In that case go with the suggestion below,

> **snowpine said:**
> CentOS and Scientific are very nice for low-end hardware.

---

### Post by Derelinquat fenestras on 2013-06-25
Thank you for your suggestions.... :)

Are CentOS and Scientific similar to Ubuntu in that certain distro versions (6.4, 5.9, 4.8, etc...) that are more stable?
Kind of like Ubuntu has LTS distros (like 12.04.1)...

Just curious before I make a selection...

Thanks again

---

### Post by snowpine on 2013-06-25
All releases of CentOS/Scientific are *extremely* stable (much more so than Ubuntu LTS, in my opinion/experience).
I recommend the current 6.4 release.

---

### Post by Derelinquat fenestras on 2013-06-25
Thank you so much, I will give it a try :)

---

### Post by |{urse on 2013-06-25
+1 for CentOs

---

### Post by mips on 2013-06-25
> **Derelinquat fenestras said:**
> Thank you so much, I will give it a try :)

Let us know how it goes and what you think of them.

---

### Post by Cheesemill on 2013-06-25
This doesn't really answer your question but you could try using the 2.9 beta version of GIMP (will be 2.10 when it is released) as this will finally have support for high bit-depth colour.

You do have to compile it yourself but there is a script available that will do this for you...
[http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/](http://www.zanshine.com/blog/stephane-richard/software/2011-10-05/cutting-edge-gimp-in-latest-ubuntu/)

Also take a look at this thread...
[http://ubuntuforums.org/showthread.php?t=2144408](http://ubuntuforums.org/showthread.php?t=2144408)

---

