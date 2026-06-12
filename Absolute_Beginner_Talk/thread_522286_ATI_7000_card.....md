---
title: "ATI 7000 card...."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-08-10
I have an ATI7000 Dual Head card that works with two monitors and extended desktop in WinXP without any issues .... but I'll be danged if I can get it to work as a true dual monitor display in Ubuntu 7.04.  I'm using the Radeon driver, not the ATI driver; this is the advice I've seen here on this board thus far.

It has the same thing on both monitors.  I've tried making the changes I've seen here but that ALWAYS results in an X-failure, forcing me to the command line.  I keep a backup of XORG.CONF and I've lost track of how many times I've restored the file so I can get back to the desktop.

Is anyone else successfully using this card with two monitors and either a) an extended desktop or b) two different displays?

Thanks! :)

(I have this sinking feeling that I'm going to have to convince my wife that I need to get another video card :( )

---

### Post by SOULRiDER on 2007-08-10
ATI cards can be a bit evil :P

Have you tried these:
[http://ubuntuforums.org/showthread.php?t=160499](http://ubuntuforums.org/showthread.php?t=160499) (bit outdated but should still work)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors) (made for Gentoo, the important part is the xorg configuration, ignore everything else, it should work)

---

### Post by moon2js on 2007-10-29
I've got the same video card and I'm trying to do the same thing.

Did Gutsy help at all for you? It didn't for me. All I can get is mirroring. On the "Screens and Graphics" panel, the second monitor parts are greyed out.

If you or anyone gets anywhere with extending desktop on this card, please post!

---

### Post by moon2js on 2007-10-29
Ooops, I just noticed I have a slightly different card, but we probably still have the same problem.

```
$ lspci -x | grep -i -e VGA -e DISPLAY
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
```

---

### Post by moon2js on 2007-11-06
> **ElEdwards said:**
> I'm using the Radeon driver, not the ATI driver; this is the advice I've seen here on this board thus far.

What's the difference between the ATI and Radeon driver? I've always been confused by this.

---

