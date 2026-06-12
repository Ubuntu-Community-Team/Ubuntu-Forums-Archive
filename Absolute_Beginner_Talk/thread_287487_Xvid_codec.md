---
title: "Xvid codec"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2006-10-28
I am trying to install Ogmrip, but I keep getting told that I don't have the Xvid codec.  I am able to play files of the Xvid compression, so I am confused to why it is saying that I don't have it.  I have installed MPlayer as well as some video codecs with Automatix, but nothing works.

Thanks for any help

---

### Post by Rackerz on 2006-10-28
Does Ogmrip come with any instructions as to what you might need?

---

### Post by chris.olsen on 2006-10-28
Here they are

glib        >= 2.6.0: [http://www.gtk.org](http://www.gtk.org)
    libxml      >= 2.0:   [http://www.xmlsoft.org](http://www.xmlsoft.org)
    dvdread     >= 0.9:   [http://www.dtek.chalmers.se/groups/dvd](http://www.dtek.chalmers.se/groups/dvd)
    mplayer     >= 0.92:  [http://www.mplayerhq.hu](http://www.mplayerhq.hu)
    mencoder    >= 0.92:  [http://www.mplayerhq.hu](http://www.mplayerhq.hu)
    ogmtools    >= 1.0:   [http://www.bunkus.org/videotools/ogmtools](http://www.bunkus.org/videotools/ogmtools)
    vorbistools >= 1.0:   [http://www.xiph.org/ogg/vorbis](http://www.xiph.org/ogg/vorbis)
    lame        >= 3.96:  [http://lame.sourceforge.net](http://lame.sourceforge.net)
    intltool    >= 0.35:  [http://www.gnome.org](http://www.gnome.org)
    pkgconfig   >= 0.12:  [http://www.freedesktop.org/software/pkgconfig](http://www.freedesktop.org/software/pkgconfig)

I had ogmrip installed on a previous install, but I believe I got the codecs all setup with EasyUbuntu, to which I can't get to run right now on Dapper.

Does anyone know of any other DVD ripping software...so I can back up my pre-existing dvds...?  I tried DVDRip, but it isn't near as easy to use as ogmrip.

Thanks

---

### Post by chris.olsen on 2006-10-28
Here is the error that I get after running ./configure
------------
checking for lame... /usr/local/bin/lame
checking for XviD support... no
configure: error: MPlayer is not build with XviD support. OGMRip requires XviD support in mplayer

but I can run XviD files in mplayer, so...

---

### Post by billl on 2006-11-13
Can you please run

$ mencoder -ovc help

and post the result ?

Thanks,

Olivier

---

### Post by chris.olsen on 2006-11-14
sorry I missed this reply.  I got by this issue, after having to reinstall ubuntu after a nasty upgrading experience.  I am now having another issue that you (Bill) already responded to.

Thanks for the help

---

