---
title: "OS with GNOME or Unity for low mem. setups"
date: 2013-01-21
forum: Any Other OS
---

### Post by joco1500 on 2013-01-21
Hello all.

I have a Dell laptop with very low memory. I love the  GNOME and Unity for  desktop setup. but i know that all of the mainstream distros (ubuntu and fedora like distros) that have them are for more resent computers. i would use ubuntu but the ones that have my wifi drivers are too slow and the ones that are fast enough for me dont have the wifi drivers.

So can someone please get me a operating system that will work for my needs? I'm sorry but i dont know exactly what wireless card i have but it is a Dell Latitude D400. 

Ya it's that old :)

---

### Post by ibjsb4 on 2013-01-21
The Dell site says that laptop comes with 128M of ram.

[Lubuntu]("http://lubuntu.net/")

Or maybe

[Puppy]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

---

### Post by Version Dependency on 2013-01-21
The only full desktop environment you could run on something with so little RAM is maybe LXDE (try Lubuntu out).  Or you might have to go with a window manager like Openbox (Crunchbang or Archbang are good Openbox distros).

---

### Post by lykwydchykyn on 2013-01-21
The desktop environment is one of the single biggest determining factors in how much RAM/CPU a distro requires.  Most of the "lightweight" distros out there are just Debian or Ubuntu with a lighter desktop.

If you want GNOME or Unity you're going to have to get hardware that can handle it.  There's no magical shortcut to making it work on old gear.

On something that old I would recommend AntiX, Vector Linux light, or just Debian stable with LXDE.

---

### Post by drawkcab on 2013-01-21
My guess is Lubuntu is even heavy for that computer.  Crunchbang or AntiX or Puppy Precise.

---

### Post by NormanFLinux on 2013-01-21
> **joco1500 said:**
> Hello all.

I have a Dell laptop with very low memory. I love the  GNOME and Unity for  desktop setup. but i know that all of the mainstream distros (ubuntu and fedora like distros) that have them are for more resent computers. i would use ubuntu but the ones that have my wifi drivers are too slow and the ones that are fast enough for me dont have the wifi drivers.

So can someone please get me a operating system that will work for my needs? I'm sorry but i dont know exactly what wireless card i have but it is a Dell Latitude D400. 

Ya it's that old :)


Try elementaryOS Luna. It works perfectly on my elderly Via chip HP MiniNote 2133 and it hardly consumes any resources. It has the specs for low powered netbook and laptop performance.

---

### Post by Max Blyss on 2013-01-21
That's a job for a Puppy.  Hands down.  MacPup would probably be pretty ideal.

---

### Post by mips on 2013-01-22
> **joco1500 said:**
> 
So can someone please get me a operating system that will work for my needs? I'm sorry but i dont know exactly what wireless card i have but it is a Dell Latitude D400. 

Ya it's that old :)

Before we carry on, how much RAM does that laptop have?
It comes standard with 128MB which is nothing but can take up to 2GB

If you only have 128MB would you be able to add say another 1GB?

Once we know how much RAM you have we can give you much better answers.

I have a similar spec laptop Celeron 1.4GHz (OC'ed to 1.87GHz) but I have 1.5GB of RAM. The CPU is a slouch but it will happily run Lubuntu or any other distro that uses Openbox etc. It could probably also run a lightweight XFCE custom setup as there is not much difference in memory usage difference between lxde & xfce if any.

---

### Post by SMOKE14 on 2013-01-22
I would recommend Puppy, or maybe Lubuntu, but that is about all that machine will handle. My 256MB machine runs Puppy pretty smoothly.

---

### Post by jwbrase on 2013-01-23
> **mips said:**
> Before we carry on, how much RAM does that laptop have?
It comes standard with 128MB which is nothing but can take up to 2GB

If you only have 128MB would you be able to add say another 1GB?

Once we know how much RAM you have we can give you much better answers.

Even 512 MB would give you enough to handle a minimal install with GNOME 2/MATE pulled in (not sure about GNOME 3 or Unity). I've got an experimental 12.04 debootstrap install with MATE, and it uses about 250 megs of RAM at a bare desktop.

---

### Post by SparkyPrawn on 2013-01-23
I've used Gnome2 on a machine with 512mbs of RAM. It wasn't perfect, but it worked.

But if your system has that low of memory, try Lubuntu as many people have mentioned. Puppy might also be the way to go for you.

---

### Post by Frogs Hair on 2013-01-23
If you would like some dock options on a light operating system Bodhi Linux may be of interest. [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by kurt18947 on 2013-01-23
If you could bring the RAM up to 512 MB. or better yet 1 GB. your choices would expand quite a bit.  I've bought RAM for old machines off Ebay.  Look for a vendor where you can return the RAM if it tests defective.  As soon as I got the Ebay RAM I installed it and let memtest run for a number of hours or overnight.  You also need to know if your Pentium M processor supports PAE.  Some do, some don't.  Some distros - Mint 14 appears to be one - require a PAE enabled processor.  I would probably install Xubuntu or Lubuntu on that machine.  I have Xubuntu 12.04 on a PIII w/ 512 MB. RAM.  It'll do everything I need except run flash.  I imagine something like transcoding video would be glacially slow.

---

### Post by kurt18947 on 2013-01-23
Duplicate

---

### Post by Nr90 on 2013-01-23
I ran Xubuntu on a very old toshiba with 128 mb ram.
It works alright for single page browsing.

On another laptop with 512 mb ram I run Debian with LXDE. It works reasonably well with chromium and up to 8 tabs open.

I would recommend Debian with LXDE. Using a lightweight or even text based browser helps.

I dislike puppy and the way it manages software etc.

---

### Post by cpatrick08 on 2013-01-24
according to [http://www.crucial.com/store/listparts.aspx?model=Latitude%20D400]("http://www.crucial.com/store/listparts.aspx?model=Latitude%20D400") you can put up to 2gb ram in your laptop

---

