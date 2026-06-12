---
title: "i want repositories for my ibook"
date: 2005-08-21
forum: Apple PPC Users
---

### Post by gumara on 2005-08-21
please tell me the good  (and have new package) repositories ppc

---

### Post by DJ_Max on 2005-08-21
I would say use the backports, but unfortunately they don't support the PPC architecture yet. What packages do you need the newest version of? Most of the time is just a matter of taking the initiative and compiling it yourself.

---

### Post by gumara on 2005-08-22
[QUOTE=DJ_Max]use the backports[/QUOTE]


backports of where

and thank you for your thread.

---

### Post by Entity on 2005-08-22
You can add these lines for backports in /etc/apt/source.list :

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

Also :

deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

The last one contains libdvdcss2, mplayer, etc. for powerpc.

Also do not forget to enable multiverse and universe repos on hoary, hoary-updates and hoary-security in /etc/apt/source.list .

---

### Post by DJ_Max on 2005-08-22
[QUOTE=Entity]You can add these lines for backports in /etc/apt/source.list :

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

Also :

deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

The last one contains libdvdcss2, mplayer, etc. for powerpc.

Also do not forget to enable multiverse and universe repos on hoary, hoary-updates and hoary-security in /etc/apt/source.list .[/QUOTE]
 Wait, backports support PPC? Last time I checked it didn't. Plus I wouldn't use Debian packages unless you want trouble.

---

### Post by Entity on 2005-08-22
[QUOTE=DJ_Max]Wait, backports support PPC? Last time I checked it didn't. Plus I wouldn't use Debian packages unless you want trouble.[/QUOTE]

I use backports on my Powerbook G4

There you go (i.e.)...
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-powerpc/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-powerpc/)

I only used the last repo in order to successfully install dvdrip (and needed transcode, etc.). You can disable it after.

---

### Post by DJ_Max on 2005-08-22
[QUOTE=Entity]I use backports on my Powerbook G4

There you go (i.e.)...
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-powerpc/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-powerpc/)

I only used the last repo in order to successfully install dvdrip (and needed transcode, etc.). You can disable it after.[/QUOTE]
 Ok, thanks, for some odd  reason I didn't know that. If I have some time, I may contribute.

---

### Post by gumara on 2005-08-23
thank you  :-)

---

