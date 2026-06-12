---
title: "How does application support work?"
date: 2007-11-09
forum: Apple PPC Users
---

### Post by ownaginatious on 2007-11-09
I'm currently debating with myself over whether I should install Ubuntu 7.10 on my iBook G4 800 MHz computer. The reason I want to switch is because OS X is in my opinion becoming more and more designed for the lowest common denomination, up to a point where I can't freakin configure anything. I got Leopard on using a very basic hack, and I really don't like the fact that I still can't read/write to my external NTFS hard drive (all 'hacks' are broken...). But this is all besides the point, here is my real question:

When I install Ubuntu onto my mac, which uses a PowerPC processor, am I only able to use programs directly compiled for PPC, or does linux work like a JVM does, where all programs made are pretty much directly compatible with all processor types? I ask because I don't want to switch to linux and not have programs like amarok, ntfs-3g, open-office, and all that due to lack of support.

Any help or opinions in making my decision to switch would be greatly appreciated. Thanks!

---

### Post by Auria on 2007-11-09
Programs are compiled natively, no VM ( except java programs, of course ;) )

I recommend you look at the PPC FAQ (sticky) for more info. The main limitations to be aware of is lack of reliable 3D drivers and no adobe flash. If you can live with that chances are you can get linux running as well or maybe even better than os x (depends on your needs and your hardware)

In doubt, you can simply try the LiveCD (7.10 has many known problems though so i personnaly use 7.04 instead) and see for yourself. You can also partition and install in dual-boot, so that you can decide later to fully switch to linux, to go back to os x or to keep both.

PS: Amarok and OpenOffice work (i don't know the other one you mentionned) and i found openOffice to work much better on linux than mac even.

---

### Post by ownaginatious on 2007-11-09
NTFS-3G is the program that gives linux support for writing to NFTS formatted hard disks. As for the 3D drivers, is their support at all? It doesn't really bother me too much since this computer only has a 32 MB ATI Radeon 9200. I think I heard about problems with those drivers though...

As for the flash thing, does YouTube run on flash? If it doesn't, then no adobe flash support doesn't really bother me. I think I read in the FAQ anyway that their is an unofficial program in development for flash support on PowerPC computers.

---

### Post by Auria on 2007-11-09
> **ownaginatious said:**
> NTFS-3G is the program that gives linux support for writing to NFTS formatted hard disks. As for the 3D drivers, is their support at all? It doesn't really bother me too much since this computer only has a 32 MB ATI Radeon 9200. I think I heard about problems with those drivers though...

As for the flash thing, does YouTube run on flash? If it doesn't, then no adobe flash support doesn't really bother me. I think I read in the FAQ anyway that their is an unofficial program in development for flash support on PowerPC computers.

Youtube does runs on flash, unfortunately. But:
- gnash is an open-source alternative that begins to support youtube (support is currently rather incomplete and buggy but in the future we can hope to get YT correctly for everyone, with future gnash versions)
- you can downlad and watch youtube videos outside the browser with a firefox extension
- i think 'democracy player' can help playing them too... (never tried myself)
in short, playing youtube is not as smooth as on mac but you can get around the problem.

As for 3D drivers, there are open-source drivers. They are not very powerful but usually it's enough for the basic tasks, the 2D and the basic 3D

I have an app called 'ntfs-3g' in my repos (i've not tried it, but it's there :) )

---

### Post by ssam on 2007-11-10
old radeon (upto r250 i think) cards have 3d acceleration.

if a linux program is open source there is about 99% chance it will work fine on linux powerpc (it needs to be compiled for powerpc, but install a powerpc distro means you get the powerpc packages).

if it is a closed source program (eg Flash, Opera, Skype, proprietry drivers) then it will only work if the company has compiled it for powerpc, and most haven't. sometimes there is an open source implementation (eg gnash and swfdec for flash), which may or may not be complete.

democracy player is called miro these days.

---

