---
title: "AMD Sempron 3000+, 64 or not?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Pi-Rat on 2006-12-27
I have searched and searched, and haven't found a clear answer yet. I have a Compaq Presario SR1000 with an AMD Sempron 3000+ processor. I am attempting a dual boot XP/Ubuntu as soon as my CDs arrive in the mail. I'm trying to save myself some time by finding out if I should use the PC or 64 installation CD. 
I can't find a clear answer as to whether or not I have the 64 setup to my processor. I've tried google, Hewlett-Packard, Compaq, and now here. Does anyone know? Will I need to use the PC version of the Dapper CD, or the 64 one?

//Pi

---

### Post by tchoklat on 2006-12-27
There a real lot of processors called 3000+ from AMD.
 
See here = [http://balusc.xs4all.nl/srv/har-cpu-amd-k7.php](http://balusc.xs4all.nl/srv/har-cpu-amd-k7.php)
 
you may need to full the cover off and check against this list
 
 
tchoklat

---

### Post by 3rdalbum on 2006-12-27
Honestly, the best way to tell is to boot up a 64-bit disc.

But really, unless you need to access more than 4 gigabytes of RAM or are doing intensive mathematical or scientific calculations, it's going to be much better for you to use the 32-bit edition. With 64-bit Ubuntu, you'll have to do some fiddling around to get proprietry applications and codecs working. If this is your first Linux installation, better to go for 32-bit.

I don't know if this helps, but my computer is an AMD Sempron 3200+. The only way I found out that it was 64-bit was by booting a 64-bit disc.

---

### Post by Pi-Rat on 2007-01-01
Thanks for the help guys.
My CDs arrived much sooner than expected, so I got to try it out. For those looking for the same answer: Sempron 3000+ is *not* 64, even though some of the higher number Semprons are.

---

### Post by gn2 on 2007-01-01
> **Pi-Rat said:**
> For those looking for the same answer: Sempron 3000+ is *not* 64, even though some of the higher number Semprons are.

Just to clear things up.....

Oh yes it is, 
[http://www.amdcompare.com/us-en/desktop/details.aspx?opn=SDA3000AIO2BX](http://www.amdcompare.com/us-en/desktop/details.aspx?opn=SDA3000AIO2BX)

Oh no it's not, 
[http://www.amdcompare.com/us-en/desktop/details.aspx?opn=SDA3000AIO2BA](http://www.amdcompare.com/us-en/desktop/details.aspx?opn=SDA3000AIO2BA)

This is a fountain of AMD info: 
[http://www.amdcompare.com/us-en/desktop/default.aspx](http://www.amdcompare.com/us-en/desktop/default.aspx)

Some of the early Socket 754 3000's were 32-bit only, but most are 64-bit compatible.

---

### Post by Pi-Rat on 2007-01-02
> Some of the early Socket 754 3000's were 32-bit only, but most are 64-bit compatible.

Yeah, in playing with the live CDs shipped to me, I found that mine is technically 64 compatible, but the CD stops running when it gets to "Creating Live CD User," even when left to run for an hour. (The drive even stopped spinning at some point.) So I guess it's still down to stick disc in and play with it. :-k

And just for giggles, I tried the Mac disc. Lethal sense of curiosity in me. :D

---

### Post by gn2 on 2007-01-02
Best to use 32-bit version anyway even with 64-bit CPU, due to difficulties getting certain things to work with 64-bit OS.

---

### Post by crazedgremlin on 2007-02-13
> **gn2 said:**
> Best to use 32-bit version anyway even with 64-bit CPU, due to difficulties getting certain things to work with 64-bit OS.

Ok, this is the exact opposite of my experience.  I use the 64-bit version because there's several problems for me with running 32-bit version.  On the install disc (live cd, not alternate (32-bit)), no usb stuff works, like my mouse, the screen resolution is horribly wrong (not a hard fix, but still), and, at least on dapper, the installation died at the keyboard setup: I could do nothing to get past it.
After these problems on the live cd, I tried the alternate cd.  It *did* install, but freaky stuff happened... it ran incredibly slow and the desktop was unable to display a background (GNOME).

I downloaded a 64-bit cd for the heck of it (I had a sneaking suspicion that my Sempron 3200+ was 64-bit) and it worked flawlessly.  No problems with proprietary codecs, graphics drivers, or anything, though I do miss flash player.

BTW, I tried 32-bit versions of numerous other distros: fedora, suse (before they got evil)...actually that's about it... I tried 2 other distros and had different problems.

Anyone else have the same experience?

A relevant afterthought: it might not be the processor, maybe there's an obscure part of my computer that is better supported in 64-bit ubuntu than in the 32-bit.  I have a compaq presario sr1610nx (cheapest computer I could find)

---

### Post by bobpur on 2007-02-13
I have an AMD 64 Athlon +3000 that wouldn't even boot reliably with the 64 bit Ubuntu but runs the 32 bit version flawlessly. I won't even consider putting the 64 bit version in it anymore.

---

### Post by vaximily on 2007-02-13
Just to clear something up about AMD vs Intel processors without linking all over the place.

Intel             --        AMD
Pentium III    --     K6 (Duron, Athlon)
Celeron        --     Sempron
Pentium 4     --    K7 (Athlon XP)
New Celeron --    New Sempron
Pentium D     --    Athlon 64  (first 64-bit i386 compatible processors for consumers)
Nothing         --    Sempron 64
Core 2 Duo    --    Athlon 64 X2
Core 2 Extreme -- Athlon 64 FX
Core 2 Quad   --   Athlon 64 4x4

Being that are running a compaq SR1000 series desktop, and you have a Sempron 3000+, I'm going to guess it is PROBABLY a Sempron 64 3000+.  To my knowledge the SR1000's didn't have any 32bit AMD processors in them.

I have a Sempron 64 2600+ that I'm running right now (along side of an Athlon 64 3000+, Core2Duo, and others).

But like other suggestions, try a 64bit bootable CD, if it works then you'll know.


On another note, I'm running Ubuntu 6.06.1 LTS Server with both Gnome and KDE and have had NO trouble what-soever.  Had to tinker with the .mpg and .wmv codecs a bit, but even a tiny amount of knowledge of command line makes that a sinch.  

Go here for a How-To for 64bit .mpg and .wmv:
[http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries](http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries)

---

