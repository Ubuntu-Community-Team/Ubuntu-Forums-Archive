---
title: "mplayer"
date: 2004-10-20
forum: Apple PPC Users
---

### Post by SyL on 2004-10-20
Hi,
I can't install mplayer on my powerbook g4. 

I add```
 deb http&#58;//honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/
```
on my sources.list

when I'm doing a apt-get install mplayer-g4 I got the following error :
```
mplayer-g4&#58; Dépend&#58; libartsc0 &#40;&gt;= 1.3.1&#41; mais 1.2.3-1 devra être installé
              Dépend&#58; libggi2 &#40;&gt;= 1&#58;2.0.5&#41; mais 1&#58;2.0.4-3 devra être installé
              Dépend&#58; libungif4g &#40;&gt;= 4.1.3&#41; mais 4.1.0b1-6 devra être installé
```

when I do a apt-get of these lib he say that the last version are installed  :?

I never used a debian system before, so I may be forget some thing ... but I think that the version of these lib -need by mplayer- aren't currently available for PPC ??!  I'm in the true ?

---

### Post by robsta on 2004-10-20
I'd suggest to "apt-get -b source" (building packages by using apt-get) the packages which are too old on your ubuntu system.
To do so you will have to add "deb-src" lines for debian unstable to your /etc/apt/sources.list

A bit tricky if you are really new to debian though.

Best luck, 
Rob

---

### Post by jBilbo on 2004-10-20
You should change that:

[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
unstable
main

to:

[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
testing
main

unstable -&gt; testing.

---

### Post by AtleO on 2004-10-21
JBilbo: The marrilat ftp contains only i386 binarys. We need PPC binarys.

/Atle

---

### Post by jBilbo on 2004-10-21
[quote=AtleO]JBilbo: The marrilat ftp contains only i386 binarys. We need PPC binarys.[/quote]

Uops, sorry :oops: 

BTW, It's curious that I had the "exactly" same error with de marrilat ftp in a x86 machine.

---

### Post by SyL on 2004-10-23
[QUOTE=robsta]I'd suggest to "apt-get -b source" (building packages by using apt-get) the packages which are too old on your ubuntu system.
To do so you will have to add "deb-src" lines for debian unstable to your /etc/apt/sources.list

A bit tricky if you are really new to debian though.

Best luck, 
Rob[/QUOTE]


Thank Rob,

when I do  *apt-get -b source libartsc0 *, I got the following error :
```

dpkg-buildpackage: source package is arts
dpkg-buildpackage: source version is 1.2.3-1
dpkg-buildpackage: source maintainer is Christopher L Cheney <ccheney@debian.org>
dpkg-buildpackage: host architecture is powerpc
dpkg-checkbuilddeps: Unmet build dependencies: automake1.8 docbook-to-man gawk libasound2-dev libaudio-dev libaudiofile-dev libesd0-dev libglib2.0-dev libmad0-dev libqt3-mt-dev libvorbis-dev sharutils texinfo xlibs-static-pic (>= 4.3.0-3)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
La commande de construction « cd arts-1.2.3 && dpkg-buildpackage -b -uc » a échoué.
E: Échec du processus fils

```

can you give me any cludes ?

thanks
-- SyL

---

### Post by Castaa on 2004-10-23
If you are going to build the source code then you are going to need to install these packages:

libasound2-dev 
libaudio-dev 
libaudiofile-dev 
libesd0-dev 
libglib2.0-dev 
libmad0-dev 
libqt3-mt-dev 
libvorbis-dev

They are used in building the source.

---

### Post by SyL on 2004-10-23
Ooupss OK 
:o

---

### Post by SyL on 2004-10-26
Ok,
   when I try to do a *apt-get -b source *for all packages need. Many of themes need other packages, which need many others ... etc ... Doesn't exist an option for use recursively this commande for all dependencies ?
   
 :-D
 []("http://www.ubuntuforums.org/images/smilies/icon_mrgreen.gif")

---

### Post by Castaa on 2004-10-26
[QUOTE=SyL]Ok,
when I try to do a *apt-get -b source *for all packages need. Many of themes need other packages, which need many others ... etc ... Doesn't exist an option for use recursively this commande for all dependencies ?
 
:-D
[/QUOTE] 
Yes.  They don't supply a lot of the deb packages for apt-get.  Possibly because those packages aren't stable.  That's a guess.
 
[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages") is a good source of packages.  It'll probably have ones you need.  Other wise Goggle them.

---

### Post by adbak on 2004-10-26
Have you tried the Multimedia Howto?  It works for me, but I have a Pentium.

I did find that using Apt/Synaptic didn't work, but the Multimedia Howto did.

---

### Post by SyL on 2004-10-27
Yes, I had already try this. The libs needs don't work with PPC,

---

### Post by SyL on 2004-10-31
Ok,
      I try vlc and now no pb   :-\"

---

