---
title: "PPC ISO too big?"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by b7j0c on 2006-06-01
i have downloaded the final PPC ISO image today and oddly enough it appears that it cannot be burned on to a normal 700MB blank CD??? did not have this problem with the 386 ISO image.

i have downloaded the ISO twice now to make sure this was not a download error of some kind.

---

### Post by rottenmac on 2006-06-01
[QUOTE=b7j0c]i have downloaded the final PPC ISO image today and oddly enough it appears that it cannot be burned on to a normal 700MB blank CD??? did not have this problem with the 386 ISO image.

i have downloaded the ISO twice now to make sure this was not a download error of some kind.[/QUOTE]

I DL'ed it and burned it in TOAST to a CD right off. 

Now if i could only get it to run.

---

### Post by hentaidan on 2006-06-01
[QUOTE=b7j0c]i have downloaded the final PPC ISO image today and oddly enough it appears that it cannot be burned on to a normal 700MB blank CD??? did not have this problem with the 386 ISO image.[/QUOTE]

Looking at the sizes the desktop PPC is 701MB. Have you tried the alternate (text based) install? Its only 692MB.

What program are you using? Most (I use graveman on Ubuntu) have an "overburn" option which squeezes those extra few MB out of the CD, and may allow you to fit 701MB onto a 700MB CD.

Dan

---

### Post by hentaidan on 2006-06-01
[QUOTE=rottenmac]Now if i could only get it to run.[/QUOTE]

Did you burn the ISO file correctly? see [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by rottenmac on 2006-06-01
[QUOTE=hentaidan]Did you burn the ISO file correctly? see [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)[/QUOTE]


yup. I installed it correctly as far as I can see. My OS X just seems to overrule the option of restarting with ubuntu. Im not sure what i need to get it to run correctly. Maybe some kernel thing or ... hell I have no idea.

I did install it OK though.

---

### Post by b7j0c on 2006-06-01
i am using nautilus in ubuntu dapper to try to burn the cd.  i am already "on" dapper, its just nice to have the live CD available.

i tried graveman, it didn't work (started duplicating from the iso, then croaked)

post-edit: on a second try, graveman works

---

### Post by savantelite on 2006-06-01
It burned fine for me, I used disk utility in mac osx

From within Mac OS X

To burn most ISOs, you can use Apple's Disk Utility (Disk Copy in older versions).

   1.Launch Disk Utility (Applications -> Utilities -> Disk Utility)
   2.Drag the ISO to the sidebar of the Disk Utility main window.
   3.Select the ISO where you just dragged it, and choose (Menu -> Image -> Burn...)
   4.Insert a blank CD and press "burn".

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by b7j0c on 2006-06-01
on osx itself i found the 'hdiutil' tool to work best:

> hdiutil burn foo.iso

---

### Post by Rxke on 2006-06-02
Hmmm, I recall I had problems too, when burning a preflight.
Maybe the older machines' (mine is a G3) optical drives don't like such 'bigger than 650Mb' disks to boot from? I very often have problems with the 700mB CDR's, when I get one from somebody else, they often read ok, but writing and then reading them myself is a crime, and probably 701 is *really* pushing the old machine's margins?

I eventually burned a 5.10, did the server-install, then changed my sources, then apt-dist upgraded from there, and then did apt-get install ubuntu-desktop (otherwise you end up downloading a lot of stuff from 5.10, only to be overwritten moments later when going to 6.06... )

---

### Post by yojimbo-San on 2006-06-03
My 6.6 ppc desktop iso wouldn't burn from the win XP machine that initially downloaded it; it claimed to be a DVD image, by which I assume it meant it was over size. WinXP doesn't actually have any ISO support, so I guess success depends on which third-party app you use.

However, I had no problems burning it from OSX 10.3.

---

### Post by chapium on 2006-06-03
I noticed the same issue with the ISO.  I was trying to burn it to a 700mb cd using the "Write to Disc..." option in Nautilus.  

I'm sure they could slim it down somehow.

:-|

---

### Post by Ptero-4 on 2006-06-03
I'm downloading Xubuntu now. The "alternate" CD is 677MB in size.

---

