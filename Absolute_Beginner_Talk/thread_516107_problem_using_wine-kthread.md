---
title: "problem using wine-kthread"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by tennisplaya05 on 2007-08-02
To start off, im running Feisty iin a 32 bit architecture.

well, i've been trying to run a playstation emulator in wine ( i already have the linux version of it; but i want to wine ePSXe for my own reasons). Only problem is that when i run it, i can't get it to find the essential video/audio plugins. My brother suggested that i use wine-kthread to run it, and this got it working for him. only problem is, whenever i try to run wine-kthread i get this:

wine: glibc >= 2.3 without NPTL or TLS is not a supported combination.
It will most likely crash. Please upgrade to a glibc with NPTL support.
Segmentation fault (core dumped)

i have glibc updated to its latest version. (i have both glibc_2.5.0-0exp1 and glibc_2.5.0-0exp2 installed) so where is the problem?

Do i need to update wine to the bleeding edge version? (im running version 0.9.42)

And could someone explain to me what kthread does?

thanks.

---

### Post by ffobsession on 2007-08-02
i think i'm newer at this than u by a million...
i downloaded the linux version of that, but its an exe and wont start O_O how did u do it?

---

### Post by tennisplaya05 on 2007-08-03
actually bud, looks like you got the windows version. you have two ways to get the linux version. If you're running feisty, it should be in the repos, so just type:

sudo aptitude install ePSXe

otherwise get it here: 
[http://www.epsxe.com/files/epsxe160lin.zip](http://www.epsxe.com/files/epsxe160lin.zip)

then get all your necessary plugins off of: 
[http://www.ngemu.com/psx/plugins.php?cat=1&os=linux](http://www.ngemu.com/psx/plugins.php?cat=1&os=linux)

.exe and .dll files are all strictly windows files. If you want to run any kind of windows file, run it through wine. and there are PLENTY of wine tutorials on these forums.

---

### Post by Hospadar on 2007-08-03
well I would first suggest you only have one version of glibc, you might look into hunting down the official glibc site (on sourceforge or wherever they happen to be) and download and build/install their own source, as whatever they have will generally be newer than what is in the ubuntu repo.

Also, if you are wondering whether or not you have the latest version of wine, I would not get it out of the ubuntu repos, but go to their website and follow their directions for an ubuntu install with their own repo.

---

### Post by tennisplaya05 on 2007-08-03
yeah, looks like i have the latest release of wine according to winehq

i was under the impression that they weren't 2 version of glibc, but were two concurrent parts of glibc. There are no conflicts, and one installs with the other. 

but i'll try getting the latest version off of the website.

---

