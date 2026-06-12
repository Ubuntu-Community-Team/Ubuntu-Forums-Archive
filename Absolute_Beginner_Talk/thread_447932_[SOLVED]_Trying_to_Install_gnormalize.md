---
title: "[SOLVED] Trying to Install gnormalize"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-18
I've downloaded and started to install gnormalize but have a few problems can anyone help please

I've extracted and changed to directory and gone to install

this line came up 
```

Install Audio-CD to play Audio CDs( you must have installed: libcdaudio,libcdaudio-devel, perl-devel )? Type (y/n):
```

I've tried to find these 3 files in Synaptic but get different files

 libcdaudio is libcdaudio1
libcdaudio-devel closest is libcdaudio-dev
and perl-dev is libperl-dev

I assume that these aren't the right files - so where do I go to find them?

I gave N as answer to the install audio cd prompt but Y to remaining options for

```
Install CDDB_get? 
Install MP3::Info? 
Install gnormalize, mppenc and mppdec?
```

Then got 
```
Sucess, install finished.
```

Which is great but when I run gnormalize I get this at the bottom of the program window

```
Can't find "lame" in executable path. The output can't be "mp3" format.
Can't find "oggenc" in executable path. The output can't be "ogg" format.
Can't find "mac" in executable path. The output can't be "ape" format.
Can't find "flac" in executable path. The output can't be "flac" format.
Can't find "faac" in executable path. The output can't be "mp4" format.
Can't find "metaflac" in executable path. 
Can't find "normalize" in executable path. The wav files can't be normalized.
Can't find "oggdec" in executable path. The input can't be "ogg" format.
Can't find "faad" in executable path. The input can't be "mp4" format.
Can't find "vorbiscomment" in executable path. 
Can't find "ogg123" in executable path. OGG files can't be played!
Can't find "play" in executable path. APE files can't be played!
```

I'm guessing that's because I've not got the three files it's looking for to install Audio CD!?

---

### Post by Happy_Man on 2007-05-18
No no, they're right-they just go by different names as the distro has....go ahead and install them.

---

### Post by forestpixie on 2007-05-18
Cheers for that - I'll have another go then - would it be best to uninstall or just reinstall over the top

If I need to uninstall how do I do that ?

TIA

---

### Post by Happy_Man on 2007-05-18
What, uninstall gnormalize? I'm not sure.... look for a readme in the source directory, it may have instructions.

---

### Post by S29K on 2007-05-18
If gnormalize is still giving you grief you can try mp3gain which is in the Universe repository.  For a GUI, there is a Java program (link below) which works very well....I've used these for about 13,000 mp3s in my collection.

[http://www.step.polymtl.ca/~guardia/javamp3gain.php](http://www.step.polymtl.ca/~guardia/javamp3gain.php)

---

### Post by forestpixie on 2007-05-18
I looked in souceforge and there's no uninstall stuff, a bug -which isn't related?

I tried to reinstall after downloading the three files - 

got this - I assume the part I've highlighted is what I need to deal with - but how I really have no idea?

If you can help I'd be grateful


```
Install Audio-CD:
Audio-CD-0.04-changed/
Audio-CD-0.04-changed/README
Audio-CD-0.04-changed/eg/
Audio-CD-0.04-changed/eg/cddb_lookup2.pl
Audio-CD-0.04-changed/eg/cdrom-play
Audio-CD-0.04-changed/CD.pm
Audio-CD-0.04-changed/cddb_lookup.c
Audio-CD-0.04-changed/MANIFEST
Audio-CD-0.04-changed/typemap
Audio-CD-0.04-changed/cddb_lookup.h
Audio-CD-0.04-changed/Makefile.PL
Audio-CD-0.04-changed/CD.xs
Checking if your kit is complete...
[COLOR="Red"]Warning: the following files are missing in your kit:
        eg/cddb_lookup.pl[/COLOR]
Please inform the author.
Writing Makefile for Audio::CD
cp CD.pm blib/lib/Audio/CD.pm
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.04\" -DXS_VERSION=\"0.04\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -g cddb_lookup.c
cddb_lookup.c:23:19: error: stdio.h: No such file or directory
cddb_lookup.c:38: error: ‘NULL’ undeclared here (not in a function)
cddb_lookup.c: In function ‘inexact_selection’:
cddb_lookup.c:52: error: ‘stdin’ undeclared (first use in this function)
cddb_lookup.c:52: error: (Each undeclared identifier is reported only once
cddb_lookup.c:52: error: for each function it appears in.)
cddb_lookup.c: In function ‘cddb_lookup’:
cddb_lookup.c:100: warning: incompatible implicit declaration of built-in function ‘malloc’
cddb_lookup.c:111: warning: incompatible implicit declaration of built-in function ‘printf’
cddb_lookup.c:113: warning: incompatible implicit declaration of built-in function ‘strncpy’
cddb_lookup.c:136: warning: incompatible implicit declaration of built-in function ‘fprintf’
cddb_lookup.c:136: error: ‘stderr’ undeclared (first use in this function)
cddb_lookup.c:152: warning: incompatible implicit declaration of built-in function ‘fprintf’
cddb_lookup.c:161: warning: incompatible implicit declaration of built-in function ‘fprintf’
cddb_lookup.c:196: warning: incompatible implicit declaration of built-in function ‘strlen’
make: *** [cddb_lookup.o] Error 1
-e 
Could not install Audio-CD.
```

as far as contacting the author - would I use the details at sourceforge ? Coming from Windows you don't get asked polite questions if it all goes belly up!

---

### Post by forestpixie on 2007-05-18
yes - thanks if this doesn't pan out i'll give it a go

---

