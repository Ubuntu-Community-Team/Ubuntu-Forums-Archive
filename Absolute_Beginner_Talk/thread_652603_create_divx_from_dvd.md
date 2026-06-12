---
title: "create divx from dvd"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-12-28
I want to rip a dvd to my hard drive and then take those files and create a divx file from them.  In windows I would use DVD Decryptor to rip the files to the HD, then Simple DivX to rip those .vob files to divx format.

I read in this forum that  these programs would work in WINE, but when I install DVD Decryptor in WINE it doesn't find my dvd drive.

So should I use something else or can someone tell me how to get DVD Decryptor to read my drive?

---

### Post by PmDematagoda on 2007-12-28
You could try DVD-rip, it can be installed using:-

```
sudo apt-get install dvdrip
```

---

### Post by kc5hwb on 2007-12-28
does this just rip? or convert to divx also?

I'll DL it now and check it out.

---

### Post by PmDematagoda on 2007-12-28
It rips the DVDs to .avi by default, but you can change it to any other format as well.

---

### Post by kc5hwb on 2007-12-28
I am trying this program and it seems to start, but then just stops after only a few seconds.  The dvd drive stops turning also and it doesn't seem to be doing anything.  Is there a repository that needs to be installed with it?

---

### Post by tor528 on 2007-12-28
you probably need css in order to decrypt the dvd.  See [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#CD.2FDVD](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#CD.2FDVD) .

basically,

sudo apt-get install libdvdread3

then 

sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by kc5hwb on 2007-12-29
I already had libdvdread3 installed.  I ran the other command and it didn't seem to help anything.  Decryptor still doesn't see my drive and dvd-rip just kinda freezes.

---

### Post by tor528 on 2007-12-29
You might try using K3b to rip, and then another program to compress.  Before anything:  check and make sure you able to play the DVD by using totem or mplayer.  If it can't play, you probably won't be able to rip it.

---

### Post by michaelzap on 2007-12-29
I use AcidRip to do this in one step (DVD to xvid/divx).

---

### Post by kc5hwb on 2007-12-29
I can play the file with mplayer.

I was able to get the dvd-rip program to work.  I took the disc out and cleaned it a bit, then I went to the Debug ->Check Dependencies in the program and installed a couple of items that it said it was missing.  That is a neat feature that I hadn't seen in other programs yet.  Anyway, after all that, it seems to be working now.  I rip the DVD to the HDD with one click, then convert those files to XviD with a second click.

I might try AcidRip to see how I like that one.

---

### Post by arman.haghi on 2008-02-12
Hey mate,

DVD::rip is very good. I've had some excellent results from it and found it very stable. You can go straight from DVD to an encoded Avi. \\:D/

As for the codec, you'll see divx 4/5 options in the enconder list, but they're not working as they're no longer supported under transcode (I believe). Which is fine; Xvid gives you great results too, just remember to use a 2 pass encode, its well worth it.

I'm pro Xvid primarily because its "Free Software and published under the GNU GPL license", and it's Free Software that has us all here in this forum in the first place, but also because it's always given me great results.

I was playing around with all this, gathered the following information, hopefully it'll be of interest:

Firstly, check this guy out for comparisons:

[http://nerds.palmdrive.net/video/Jan2006/index.html](http://nerds.palmdrive.net/video/Jan2006/index.html)

And some other info:

1. Both DivX and XviD support each other
2. Playing quality is pretty much the same
3. Xvid [is] less obtrusive and lighter
4. DivX(tm) includes spyware and crap which you probably don't want
5. XviD on the otherhand doesn't but the filter isn't really optimized and has some backwards compatibility issues
6. "ffdshow" is worth a look also
7. "XviD encoded files can be ... played in a DivX compatible DVD player, as long as they are not ... using features unsupported by DivX (e.g. three warppoints instead of one), since such features are not considered "MPEG-4 compliant" by DivX."(1.5)

IMHO, the basic thing is to use two-pass and you're probably going to get a very good, very similar result from either.

Sources:
  [http://en.wikipedia.org/wiki/XviD](http://en.wikipedia.org/wiki/XviD)
 [http://www.velocityreviews.com/forums/t373273-divx-vs-xvid.html](http://www.velocityreviews.com/forums/t373273-divx-vs-xvid.html)
  [http://club.cdfreaks.com/f3/divx-vs-xvid-128001/](http://club.cdfreaks.com/f3/divx-vs-xvid-128001/)
  [http://nerds.palmdrive.net/video/Jan2006/index.html](http://nerds.palmdrive.net/video/Jan2006/index.html)

---

