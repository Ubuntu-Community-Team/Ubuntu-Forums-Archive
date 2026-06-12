---
title: "Just bought a new computer.  will ubuntu work?"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by kook44 on 2005-09-23
Ok, So I bit the bullet and upgraded from my 5 year old P3 733, which ubuntu installed and ran very nicely on, without a single hitch.

I bought a dell dimension 9100.  2 things that concern me:

1)The proccessor is a pentium D w/ dual core.  Will ubuntu run on that?  I hear there is another kernel you must use for dual core processors?  I consider myself a techie, but using a different kernel might be out of my league...

2)The graphics card is 128MB PCI Express™ x16  ATI Radeon X300 SE w/ HyperMemory.  I realize that ATI is not natively supported in linux.  I can search for the how-to's, but can someone just give me the gist of what, essentialy, needs to be done? ie- use a 3rd party or open-source driver for minimal support?  Or is there a way to get the full resolution out of the card (I got the 24" widescreen monitor - would like to take full advantage of that)

PS - I'm not a gamer, but I am a programmer and web developer, so while 3D animation isn't superbly important, sharp, clean graphics are.

THX!

---

### Post by PsyberOneZero on 2005-09-23
For the first part, you should be fine using the stock kernel SMP version, most dual-core processors are seen as 2 processors but most OS's. That shouldn't be a big problem.

The ATI card migth give you some troubles. You need to make sure that you get the fglrx drivers. According to ATI

> The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as FireGL 8700 and later products.
We do not currently plan to include support for any products earlier than this.
Drivers for earlier products should already be available from the DRI Project or Utah-GLX project.

but until you get that and linux-restricted-modules installed you may either need to use the VESA driver or install the packages in console.

Good Luck!

---

### Post by phen on 2005-09-23
afaik there are ati drivers included in hoary. while they support ati cards well in 2D, they do not offer hardware accelleration. just try it with the live cd!

---

### Post by mlomker on 2005-09-23
> 2)The graphics card is 128MB PCI Express™ x16  ATI Radeon X300 SE w/ HyperMemory.  I realize that ATI is not natively supported in linux.  I can search for the how-to's, but can 

Your machine will probably boot up using the ATI drivers, which will put a display on your screen and work just fine.  If you want to play games then you need to install the drivers, which can be a little bit of work.

I have a [detailed how-to](http://www.ubuntuforums.org/showthread.php?p=348911) on how to accomplish that.

---

### Post by mlomker on 2005-09-23
> 2)The graphics card is 128MB PCI Express™ x16  ATI Radeon X300 SE w/ HyperMemory.  I realize that ATI is not natively supported in linux.  I can search for the how-to's, but can 

Your machine will probably boot up using the ATI drivers, which will put a display on your screen and work just fine.  If you want to play games then you need to install the 3D drivers, which can be a little bit of work.

I have a [detailed how-to](http://www.ubuntuforums.org/showthread.php?p=348911) on how to accomplish that.

---

### Post by PsyberOneZero on 2005-09-23
I had problems with an nVidia PCI-E 16x card, it would load with nv, then freeze, vesa looked horrible, it wasn't 'till I got the official drivers that it really worked.  It's not the card itself but the PCI-E 16x that was hanging it up it's just slightly too new right now. I would assume that an ATI PCI-E card would have similar issues.

---

### Post by jasay on 2005-09-23
To give you some hope, my (slightly older) x300 card works just fine with the proprietary ATI drivers (8.16.20).  Took a little work, but I just followed the howtos and it's been all smiles since. :)

---

### Post by PsyberOneZero on 2005-09-23
I didn't mean to scare anyone off, I'm sure that if you follow **mlomker**'s tutorial and just take it step by step you should be fine, ubuntu is one of the most flexible and "Ready out of the box" distros I've ever used. I was just saying that the PCI-E *may* be an issue

BTW: **mlomker** Awesome tutorial, I wish that was out when I had my laptop w/ FireGL T2

---

