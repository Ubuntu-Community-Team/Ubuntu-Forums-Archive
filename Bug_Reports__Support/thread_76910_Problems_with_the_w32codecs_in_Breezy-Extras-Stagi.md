---
title: "Problems with the w32codecs in Breezy-Extras-Staging"
date: 2005-10-15
forum: Bug Reports / Support
---

### Post by Darrena on 2005-10-15
It seems like it tries the same mirror over and over again, that mirror is currently down so it is on try#8 and continues to fail.

Is there a way to have it try multiple mirrors?

Thanks!

---

### Post by macleod199 on 2005-10-21
I'm seeing this problem too. Any easy way to edit the mirror?

---

### Post by ubnoobie on 2005-10-28
[QUOTE=Darrena]It seems like it tries the same mirror over and over again, that mirror is currently down so it is on try#8 and continues to fail.

Is there a way to have it try multiple mirrors?

Thanks![/QUOTE]



i *just* finished dealing with this same thing a few minutes ago...

here's what i did:


go to [www.mplayerhq.hu]("http://www2.mplayerhq.hu/homepage/design7/codecs.html") and find a working download link for this file:
Windows all  	all codecs for Windows (Win32 .dll)  	20050412  	12M  windows-all-20050412.zip

this is the one i used:
[http://www2.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip](http://www2.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip)

[download the deb file separately]("http://cdn.mirror.garr.it/mirrors/ubuntu-backports/dists/breezy-extras-staging/restricted/binary-i386/w32codecs_20050412+breezy0.0.1_all.deb") from
[http://cdn.mirror.garr.it/mirrors/ubuntu-backports/dists/breezy-extras-staging/restricted/binary-i386/](http://cdn.mirror.garr.it/mirrors/ubuntu-backports/dists/breezy-extras-staging/restricted/binary-i386/)


in a terminal/console session..
either sudo everything below or enter a root session:  sudo su -

cd to where you downloaded the package.

unpack the deb without running the script:
**[SIZE="4"][FONT="Courier New"]dpkg --unpack w32codecs_20050412+breezy0.0.1_all.deb[/FONT][/SIZE]**


edit the postinst script to reflect the different download location:
**[SIZE="4"][FONT="Courier New"]nano -w /var/lib/dpkg/info/w32codecs.postinst[/FONT][/SIZE]**

change the url in the wget statement to point to the working download you found (above).

mine ended up being:
```

#!/bin/sh
set -e
cd /tmp
wget -c http://www2.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip
mkdir -p /usr/lib/win32
unzip -j windows-all-20050412.zip -d /usr/lib/win32
rm windows-all-20050412.zip

```

install the already extracted, and now modified, package:
**[SIZE="4"][FONT="Courier New"]dpkg --configure w32codecs[/FONT][/SIZE]**


all done.


there is likely a "better" way.. this is just what i did. 


more about dpkg can be found
[http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)


msttcorefonts had the same problem awhile back (and has since changed to support multiple download sites).

---

### Post by cmsj on 2005-11-01
Erk, that is quite a scary solution. You really shouldn't be overwriting packaged files in the postinst.
You could just install from a tarball or grab the .deb of 20050412 from:

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/)

---

### Post by jdong on 2005-11-09
The simple way to do it is to **download that file to /tmp**. The installer will automatically pick it up.


Yes yes I know there are major security issues with that setup, which is why the package is *staging*... 

May I also suggest PLF for illegal backports, since I do not like the legal risk associated with them and likely will not package more for Extras.

---

