---
title: "Screwed up a system file, need to restore"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by John Jason Jordan on 2005-06-16
In an effort to get DVD players (Totem, MPlayer, VLC, Ogle) to play movies, I searched the wikis here and discovered that I needed to run install-css.sh, which is evidently a script. Unfortunately, the author of that advice did not realize that a total n00b like me would have no idea how to "run" a script. So from a root terminal I tried various things. None worked. Worse, one of the things I tried was "script install-css.sh." Guess what that command did? It overwrote the original script file with a zero byte file.

So now I need to restore the original script file. I don't want to go all the way through reinstalling Ubuntu just to get one file back. And, since I have no files created on this computer yet, I haven't bothered to learn how to do backups, so there is no backup to do a restore from. (Note to self: Scope out backups pronto.)

Is there a place where I can download just this one one little file?

---

### Post by Xian on 2005-06-16
I would appear that script came from the /usr/share/doc/libdvdread3/examples/ path.
Just copy and save as install-css.sh

```
#!/bin/sh
set -e

site=http://www.dtek.chalmers.se/groups/dvd/deb/
arch=$(dpkg --print-installation-architecture)

soname=2
uversion=1.2.5
available="alpha hppa i386 ia64 powerpc s390 sparc"
version=${uversion}-1

if ! type wget > /dev/null ; then
    echo "Install wget and run this script again"
    exit 1
fi

for a in $available; do
    if [  "$a" = "$arch" ]; then
	wget ${site}libdvdcss${soname}_${version}_${arch}.deb -O /tmp/libdvdcss.deb
	dpkg -i /tmp/libdvdcss.deb
	exit $?
    fi
done

echo "No binary deb available.  Will try to build and install it."
echo "You need to have debhelper, dpkg-dev and fakeroot installed."
echo "If not, interrupt now, install them and rerun this script."
echo ""
echo "This is higly experimental, look out for what happens below."
echo "If you want to stop, interrupt now (control-c), else press"
echo "return to proceed"
read dum

mkdir -p /tmp/dvd
cd /tmp/dvd
wget ${site}libdvdcss_${uversion}.orig.tar.gz
wget ${site}libdvdcss_${version}.diff.gz
wget ${site}libdvdcss_${version}.dsc
dpkg-source -x libdvdcss_${version}.dsc
cd libdvdcss-${uversion}
fakeroot ./debian/rules binary
echo "Any problems?  Interrupt now (control-c) and try to fix"
echo "manually, else go on and install (return)."
dpkg -i ../libdvdcss${soname}_${version}_${arch}.deb
```

---

### Post by John Jason Jordan on 2005-06-17
Thanks. As it turned out, later in the day I screwed up X trying to follow another wiki how-to here. I ended up having to reinstall. 

So now I have the file back. I've looked all over, but how do I "run" a script?

---

### Post by Xian on 2005-06-17
[QUOTE=John Jason Jordan]Thanks. As it turned out, later in the day I screwed up X trying to follow another wiki how-to here. I ended up having to reinstall. 

So now I have the file back. I've looked all over, but how do I "run" a script?[/QUOTE]
Basically you can either put it in /usr/bin, take off the trailing extention '.sh', make it executable and run it from any command line, or you can just cd to the script location and run it from there (if executable). Some scripts have further option parameters that must be used in order to run it properly and those are generally commented right in the script text. In this case it would be:

```
 $ cd /usr/share/doc/libdvdread3/examples/
$ sudo ./install-css.sh
```

---

