---
title: "Linux for Amiga 1200"
date: 2012-06-30
forum: Any Other OS
---

### Post by ayenack on 2012-06-30
Hello all.

Pre-amble

Many years ago I gave my Amiga 1200 to my brother, the other day I was helping him clear his garage and we came across that same old Amiga I ended bringing it home as he was going to bin it and I couldn't see it binned (it gave me many years of pleasure).


I've been wondering what I'm going to do with this old lump of nostalgia and I suddenly remembered that some souls had put Linux on their 1200's...

So the question is... does anyone know of an old or still maintained distro that I can stick on this old Amiga 1200.

Thanks in advance for any help, would love to do something with this old old box.

ayenack.

---

### Post by |{urse on 2012-06-30
Now I've never done this but I'm going to guess slitaz would work. 30mb and all the drivers are there. I'm sure video will be an issue and you will need to set some bootflags.

---

### Post by ayenack on 2012-06-30
Thanks |{urse SliTaz seems to be a Intel/AMD distro the old Amiga is PPC so no joy with that.

Have found a possibility though it called [uClinux]("http://www.uclinux.org/index.html").

Would still like other suggestions if anyone has got any.

Thanks.

---

### Post by CrocoDuck on 2012-06-30
> **ayenack said:**
> Hello all.

Pre-amble

Many years ago I gave my Amiga 1200 to my brother, the other day I was helping him clear his garage and we came across that same old Amiga I ended bringing it home as he was going to bin it and I couldn't see it binned (it gave me many years of pleasure).


I've been wondering what I'm going to do with this old lump of nostalgia and I suddenly remembered that some souls had put Linux on their 1200's...

So the question is... does anyone know of an old or still maintained distro that I can stick on this old Amiga 1200.

Thanks in advance for any help, would love to do something with this old old box.

ayenack.

Yo \\:D/ ! You touched my soul with that, bro! Me and my brother had an amiga 500... And gazillions of floppy full of gameS... I have read on an italian page of amiga enthusiastics that this should work:

LinuxPPC 1999 Q3 (APUS+RedHat 5.1 PPC)   ([http://www.amiworld.it/amigalinux/amigalinux.html](http://www.amiworld.it/amigalinux/amigalinux.html))

Maybe you can find all the stuff here: [http://www.jonh.net/lppcfom-serve/cache/377.html](http://www.jonh.net/lppcfom-serve/cache/377.html)

Have a look at here: [http://penguinppc.org/](http://penguinppc.org/) , [http://www.linux-m68k.org/](http://www.linux-m68k.org/) , [https://fedoraproject.org/wiki/Fedora_17_PPC_release_notes](https://fedoraproject.org/wiki/Fedora_17_PPC_release_notes) . There are also a Debian, an Arch and an OpenSuse ports for PPC: [http://www.archlinuxppc.org/](http://www.archlinuxppc.org/), [http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/) , [http://download.opensuse.org/distribution/11.1/iso/](http://download.opensuse.org/distribution/11.1/iso/)

---

### Post by rai4shu2 on 2012-06-30
> **ayenack said:**
> Thanks |{urse SliTaz seems to be a Intel/AMD distro the old Amiga is PPC so no joy with that.

Have found a possibility though it called [uClinux]("http://www.uclinux.org/index.html").

Would still like other suggestions if anyone has got any.

Thanks.

If it's still a vanilla Amiga 1200, that would make your CPU a 68020. I highly doubt that could run Linux.

If that is the case, you could possibly cross compile something like Haiku, although I don't know how well that would go.

See [http://www.haiku-os.org/guides/building](http://www.haiku-os.org/guides/building)

---

### Post by khelben1979 on 2012-06-30
> **rai4shu2 said:**
> If it's still a vanilla Amiga 1200, that would make your CPU a 68020. I highly doubt that could run Linux.

It's possible to run old [Debian 2.1]("http://www.debian.org/releases/slink/") "Slink" on a standard Amiga 1200... Forget about running graphics, though.

I installed [Debian 2.2]("http://www.debian.org/releases/potato/") "Potato" and ran it on an Amiga 4000 equipped with PPC processor back in -99. And for this I saw a big difference in performance going from 64 MB of RAM memory upto 128 MB where running the X server had a lot faster performance. 3D hardware acceleration with the CybervisionPPC was and is possible using the Linux APUS kernel.

---

### Post by ayenack on 2012-06-30
Thanks for all the replies everyone.

My brother has now found the box of games and apps that I gave to him with the Amiga so I think for now that I'll take a trip down memory lane and play some of the old games particularly, Pirates, Rubicon, Uridium 2 (my favorite shoot em up of all time) and Zool, platform glory here I come also will be joining the Frontier Elite.

> Yo  ! You touched my soul with that, bro! Me and my brother had an amiga 500... And gazillions of floppy full of gameS...

Thanks. 

Memories of yesteryear... Happy, Happy days! Now all I've got to do is get my old C64 back and play text adventure Luxor LOL.

---

### Post by avongil on 2012-06-30
I think you will be better served running AmigaOS. I installed NetBSD on a similar spec machine - Mac IIcx, a 16mhz 68030.  [http://en.wikipedia.org/wiki/Macintosh_IIcx](http://en.wikipedia.org/wiki/Macintosh_IIcx)

It was horribly slow with a stripped down install of NetBSD of 1998.  Directory listings were so slow, it reminded me of an Apple IIe. 

It was fun to get installed and working, but after that there is little to do.

---

