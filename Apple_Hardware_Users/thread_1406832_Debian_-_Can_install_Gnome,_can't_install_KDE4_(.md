---
title: "Debian - Can install Gnome, can't install KDE4 :("
date: 2010-02-14
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2010-02-14
Hello. I got the image for KDE on Debian for powerpc here:

[http://www.debian-desktop.org/pub/linux/debian/kde43-live/](http://www.debian-desktop.org/pub/linux/debian/kde43-live/)


When I run it live, I see KDE4. When I install it off the same disk, it installs Gnome. I can't figure out how to install KDE4. I had no luck with apt-get install kde4 (E: Couldn't find package kde4), no luck with aptitude, no luck with Synaptic (The following packages have unresolved dependencis... kdebase-runtime-bin-kde4).

Can someone help me? Stupid question but is it because I had the image burned on a DVD-RW?

Thanks, Chris

---

### Post by linuxopjemac on 2010-02-14
I guess a:
```

sudo apt-get install kubuntu-desktop
```

will do the job, you can then later decide to remove gnome:

```
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

```

This is for (K)Ubuntu, sorry for not reading ;)

---

### Post by oswaldkelso on 2010-02-14
Kubuntu? Not on Debian.

There is no official Debian live CD for PPC 

Try the Debian-live unoffical PPC release. But I didn't think you could install from it?

[http://live.debian.net/cdimage/release/5.0.3-unofficial/powerpc/iso-cd/](http://live.debian.net/cdimage/release/5.0.3-unofficial/powerpc/iso-cd/)

I you want to install just do a net install and upgrade to KDE4 from backports

build from a testing net install [http://cdimage.debian.org/cdimage/release/5.0.4/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/release/5.0.4/powerpc/iso-cd/)

or go straight to testing

[http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/)

KDE4 is dog slow on my G4 800 (unless I turn every bit of bling off) Even then noticeably slower than XFCE which is almost snappy with everything on.

---

### Post by Chris Grk-O-Matic on 2010-02-15
Thanks for those links - I never would of found them in a million years. I'll try them out and see how it goes



I should have mentioned the hardware earlier:

1Ghz Titanium PowerBook
1gig RAM

---

