---
title: "problem compiling fluxbox"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-05-19
```

wr0x2@USSENTERPRISE:~/Desktop/fluxbox-0.1.14$ make
cd . \
  && CONFIG_FILES= CONFIG_HEADERS=config.h \
     /bin/sh ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14'
Making all in data
make[2]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data'
Making all in styles
make[3]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data/styles'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data/styles'
make[3]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data'
../util/fluxbox-generate_menu -o menu -p /usr/local/share -m "Fluxbox-0.1.14"
sed -e "s,@pkgdatadir@,/usr/local/share/fluxbox,g" init.in > init
make[3]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data'
make[2]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/data'
Making all in doc
make[2]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/doc'
sed -e "s,@pkgdatadir@,/usr/local/share/fluxbox," fluxbox.1.in > fluxbox.1
make[2]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/doc'
Making all in nls
make[2]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls'
Making all in C
make[3]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls/C'
make[3]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls/C'
Making all in da_DK
make[3]: Entering directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls/da_DK'
Translation.m:8: invalid character: message ignored
Translation.m:9: invalid character: message ignored
Translation.m:24: invalid character: message ignored
Translation.m:27: invalid character: message ignored
Translation.m:28: invalid character: message ignored
Translation.m:29: invalid character: message ignored
Translation.m:31: invalid character: message ignored
Translation.m:32: invalid character: message ignored
Translation.m:55: invalid character: message ignored
Translation.m:65: invalid character: message ignored
Translation.m:67: invalid character: message ignored
Translation.m:108: invalid character: message ignored
Translation.m:110: invalid character: message ignored
Translation.m:117: invalid character: message ignored
Translation.m:121: invalid character: message ignored
Translation.m:129: invalid character: message ignored
Translation.m:130: invalid character: message ignored
Translation.m:131: invalid character: message ignored
Translation.m:132: invalid character: message ignored
Translation.m:148: invalid character: message ignored
Translation.m:160: invalid character: message ignored
Translation.m:163: invalid character: message ignored
Translation.m:168: invalid character: message ignored
Translation.m:169: invalid character: message ignored
Translation.m:170: invalid character: message ignored
Translation.m:185: invalid character: message ignored
Translation.m:186: invalid character: message ignored
Translation.m:187: invalid character: message ignored
Translation.m:188: invalid character: message ignored
Translation.m:202: invalid character: message ignored
Translation.m:203: invalid character: message ignored
make[3]: *** [fluxbox.cat] Error 1
make[3]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls/da_DK'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14/nls'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wr0x2/Desktop/fluxbox-0.1.14'
make: *** [all] Error 2

```

Yeah wtf. I googled the errors and they all seem to be coming from people compiling blackbox. Can anyone help?

---

### Post by catlett on 2006-05-19
This thread might help with installing fluxbox,  although it doesn't deal with the problem your having. [http://ubuntuforums.org/showthread.php?t=111157](http://ubuntuforums.org/showthread.php?t=111157)

---

### Post by wr0x2 on 2006-05-19
I don't really want to install from a binary, because last time I did there were some severe configuration issues. My last fluxbox install compiled flawlessly once I got all the deps, although it might have been a different version.

---

### Post by jpkotta on 2006-05-19
I tried compiling fluxbox just for fun, and it failed just like yours did.  I tried the latest unstable (0.9.15.1), and that compiled just fine.  I didn't run it though (because I use fvwm, and have no want of another WM), but the fluxbox site says it's probably better than 0.1.14.x.

---

### Post by wr0x2 on 2006-05-19
Thanks, I wasn't really paying attention on their download page.

---

### Post by Sef on 2006-05-20
Here's a howto on installing fluxbox from source.

[http://doc.gwos.org/index.php/FluxboxSource]("http://doc.gwos.org/index.php/FluxboxSource")

---

