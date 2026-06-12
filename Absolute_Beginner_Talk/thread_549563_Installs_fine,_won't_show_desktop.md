---
title: "Installs fine, won't show desktop"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Brandon2520 on 2007-09-12
I've tried installing 7.04 64 bit, i386 and the alt install. I also tried installing 6.06.1 i386 version and all have the same problem. I'm dual booting ubuntu and win xp. Install works perfectly and I get the boot selection screen ok. Ubuntu seems to load fine as far as the login screen, it recognizes my pass and username but then dies. My desktop consists of a tan-ish color and some garbled pixels in the center. Not start bar, icons, nothing. I can move my mouse around ok though. I figure its some sort of hardware compatibility issue? My hardware is as follows:

7800GTX OC
Fatality mobo nvidia chipset
250 gig maxtor
intel core 2 duo


Any ideas?

---

### Post by tyler22 on 2007-09-12
Does it show a desktop when running form the cd?

---

### Post by bsharp on 2007-09-12
Hey you took my name :mad:

Anyway.....

> **Brandon2520 said:**
> I've tried installing 7.04 64 bit, i386 and the alt install. I also tried installing 6.06.1 i386 version and all have the same problem. I'm dual booting ubuntu and win xp. Install works perfectly and I get the boot selection screen ok. Ubuntu seems to load fine as far as the login screen, it recognizes my pass and username but then dies. My desktop consists of a tan-ish color and some garbled pixels in the center. Not start bar, icons, nothing. I can move my mouse around ok though. I figure its some sort of hardware compatibility issue? My hardware is as follows:

7800GTX OC
Fatality mobo nvidia chipset
250 gig maxtor
intel core 2 duo


Any ideas?

Have you tried booting into a recovery kernel?  If you can do this first:
```
startx
```

If that doesn't work, try this:
```
dpkg-reconfigure x11-common
```

---

### Post by bsharp on 2007-09-12
just a note:
doing the startx thing will log you into GNOME as root, I only suggested that option to see if it works with a recovery kernel. Even if it does work, you will probably have to do the second option anyway.

---

### Post by Brandon2520 on 2007-09-13
No luck :(

Same scrambled looking screen with startx.


Wish I had a second graphics card to try out and see if that's the problem.


Oh, and no it doesn't boot form the live cd either. Same garbled crap.

---

### Post by splintercellguy on 2007-09-13
What video card do you have? Have you tried doing this in Recovery Mode?

dpkg-reconfigure xserver-xorg

Perhaps you should try Envy for latest Nvidia drivers.

---

### Post by Brandon2520 on 2007-09-13
I've got the 7800GTX OC (I think it was evga)


If I download new drivers and burn to cd, is there a way to install without being able to get into the os? I'd imagine it's a simple command line command.... only been doing unix commands for 3 weeks now though.

---

