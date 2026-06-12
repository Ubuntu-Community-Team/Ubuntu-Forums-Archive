---
title: "is multi-media dead to linux? Legal issues"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by grimmson on 2005-10-05
Hello all. I'm trying to get codecs ,libdvdcss2 and other stuff from the guide. Nothing is downloading xsept divx I think. I've tried the forums and all links so far (dated as early back as 5 days ago are dead.) Should I stop trying to follow the guide for all codecs?:confused:

---

### Post by mlomker on 2005-10-05
You can add this repository for libdvd:

```

deb ftp://ftp.nerim.net/debian-marillat unstable main

```

You can get the win32 codecs from the [Mplayer website.]("http://www1.mplayerhq.hu/homepage/design7/codecs.html")

---

### Post by poofyhairguy on 2005-10-05
[QUOTE=mlomker]You can add this repository for libdvd:
```

deb ftp://ftp.nerim.net/debian-marillat unstable main

```
You can get the win32 codecs from the [Mplayer website.]("http://www1.mplayerhq.hu/homepage/design7/codecs.html")[/QUOTE]


If you add that repo, take it away when you are done. Upgrading with it in can break Ubuntu.

There is the w32codecs:

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

---

### Post by mlomker on 2005-10-05
> If you add that repo, take it away when you are done. Upgrading with it in can break Ubuntu.


A good point.  I just noticed that they have gstreamer and a few other things in that repository.  It's generally a good practice to remove any non-ubuntu repository once you have downloaded the file that you are looking for.

---

### Post by grimmson on 2005-10-05
great info guys. thanks for the heads up.

---

