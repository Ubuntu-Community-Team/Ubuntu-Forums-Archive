---
title: "Gimmie"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2007-11-23
[http://www.ubuntugeek.com/gimmie-a-new-panel-for-gnome-installation-in-ubuntu.html](http://www.ubuntugeek.com/gimmie-a-new-panel-for-gnome-installation-in-ubuntu.html)

I followed this how-to and was good all the way until i got to make check.  ./configure was good and make was good and as far as i could tell installing all the dependencies and requirements mentioned in the hack were fine too. 

However, when i did make check before the final make install command i got knocked off my horse.

I get: 

livingdaylight@Hod:~/gimmie-0.2.1$ make check
Making check in data
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/data'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/data'
Making check in gdmclient
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/gdmclient'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/gdmclient'
Making check in gnomecups
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/gnomecups'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/gnomecups'
Making check in iconentry
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/iconentry'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/iconentry'
Making check in sexy
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/sexy'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/sexy'
Making check in traymanager
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/traymanager'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/traymanager'
Making check in po
make[1]: Entering directory `/home/livingdaylight/gimmie-0.2.1/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[1]: *** [ar.gmo] Error 127
make[1]: Leaving directory `/home/livingdaylight/gimmie-0.2.1/po'
make: *** [check-recursive] Error 1
livingdaylight@Hod:~/gimmie-0.2.1$ 

what is Error 127 and can anyone translate the meaning of this output to me, please? Has anyone else come across this error?

thank you very much in advance for any help given

--

sophtpaw

---

### Post by sophtpaw on 2007-11-23
In addition i wondered whether i would need Compiz or in any case a 3D enabled Desktop. As i do not, i wonder whether this could also the source of my difficulty???

---

### Post by Ub1476 on 2007-11-23
I think Gimmie is in the repos.

```
sudo apt-get install gimmie
```

---

### Post by sophtpaw on 2007-11-23
> **Ub1476 said:**
> I think Gimmie is in the repos.

```
sudo apt-get install gimmie
```

LOL now i feel stupid... yes, it is. I thought i checked and didn't find it; must have left out an 'm' in gimmie or misspelt it some other way. but now i see that it is. version 0.2.7

Thank You

Incidentally, coming back to my original install attempt from the ubuntukeek.com hack my misstake was to try to install gimmie 0.2.1 and failed to get teh latest 0.2.8 i still encountered problems nonetheless, al be it different ones.

again ./configure is fine but the next stage 

'make' gets me 

livingdaylight@Hod:~/gimmie-0.2.8$ make
make: *** No targets specified and no makefile found. Stop.

and so the next step obviously doesn't work either

'make check'

livingdaylight@Hod:~/gimmie-0.2.8$ make check
make: *** No rule to make target `check'. Stop.


Anyways, its great that it is in repos anyways, even if it is not the latest release version, but curious still nonetheless now, having tried, to know why i haven't been able to compile this from source?? :confused:

---

### Post by Goombie on 2007-11-25
If you really want the latest version of Gimmie, you can download it from [www.getdeb.net](www.getdeb.net). No need to fuss with compiling it then. :popcorn:

---

### Post by Perfect Storm on 2007-11-25
Tested for 64-bit: (as getdeb .deb is for 32bit)

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential intltool libtool checkinstall
sudo aptitude install python2.5-dev libgnomecups1.0-dev python-gtk2-dev python-gobject-dev libgtk2.0-dev libdbus-1-dev libgnome2-dev libgnomevfs2-dev libpanel-applet2-dev libwnck-dev python-gmenu


cd ~/Desktop
wget http://www.beatniksoftware.com/gimmie/releases/gimmie-0.2.8.tar.gz
tar zxfv gimmie_0.2.8.orig.tar.gz
cd gimmie-0.2.8.orig
./configure --prefix=/usr
make
sudo checkinstall
```

---

