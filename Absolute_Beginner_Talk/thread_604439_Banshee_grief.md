---
title: "Banshee grief"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-11-06
Hey there recently(yesterday) banshee had a gnarly crash, took like 5 mins to force quit, since then it doesnt play music anymore, no error reports were generated in /var/crash either, so! i reinstalled banshee but it still doesnt play music anymore, 

ok, so ive tried dl the SVN release from the banshee site, but when i do:

 ./autogen.sh --prefix=/usr

to install the SVN, i get this:

checking for MUSICBRAINZ... configure: error: Package requirements (libmusicbrainz >= 2.1.1) were not met:

No package 'libmusicbrainz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUSICBRAINZ_CFLAGS
and MUSICBRAINZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


ok, so i checked to see where this 'libmusicbrainz' was in synaptic, turns out i have it installed already, so i reinstalled it to be sure(its called libmusicbrainz4c2a)

and yet still no luck, if anybody out there knows the solution please tell me, help much appreciated


PS - i dont want to use an alternative like rythmbox or whatever, i like banshee and want to get it working again!

---

### Post by dynamethod on 2007-11-06
please help! ive tried both the tarball and SVN, neither work!

---

### Post by dynamethod on 2007-11-06
OMFG, this is EXCRUTIATINGLY painfull to install! im having to install EACH AND EVERY dependancy everytime it complains about one, and there not at all easy to find in synaptic!, it wants the -dev packages for the dependancies too! man theres GOT to be a easier way to get banshee back! someone please please tell me how to get it working again!!!

---

