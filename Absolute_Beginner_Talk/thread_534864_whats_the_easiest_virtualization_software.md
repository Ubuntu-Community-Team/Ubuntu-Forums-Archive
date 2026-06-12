---
title: "whats the easiest virtualization software?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-08-25
ok, so i dont have any hardware for virtualization in my athlon 2800.  but whats the BEST and easiest virtualization software?

---

### Post by rbprogrammer on 2007-08-25
you could try "virtual box"..  i think it is even in the repositories, so if you dont like it it will be easy to uninstall.

sorry i can't elaborate on the specifics of virtual box since i have not tried it yet myself.  i only installed it, just never installed another OS yet.  the only thing i can say is that it is free.  others like vmware, cadega (for gaming), win4lin, all cost money, so i never tried them.

hope that helps you, or at least gets you going in a direction.

---

### Post by nonewmsgs on 2007-08-25
virtualbox definitely
there are actual 2 virtual boxes.  one in the repositories and one on their site that is under a different license with a few other features.

---

### Post by rbprogrammer on 2007-08-25
> **nonewmsgs said:**
> virtualbox definitely
there are actual 2 virtual boxes.  one in the repositories and one on their site that is under a different license with a few other features.

do you know the other name off the top of your head??  i'd like to try it when i need to install windoze..  if not, i think i could find it.  i'll do a search for "virtualization" or some varient..

---

### Post by nonewmsgs on 2007-08-25
vmware?  if you look up in ubuntu you can find a thread i started with a list of errors i got when trying it...i never did get it working.

oh you mean the other version? it's also called vmbox but it's on the vmbox website.  it has some things like usb support

---

### Post by capink on 2007-08-26
Try virtualbox first. It is easier than other alternatives. Be sure to not to get the open source version as it lacks two essential features: folder sharing and usb support. To get the binary version add the following line to your sources.lst

```
deb http://www.virtualbox.org/debian feisty non-free
```

Note: Replace feisty with edgy if you are on ubuntu 6.10

---

### Post by Bazirker on 2007-08-27
Yeah definetly don't get the open source version of Virtualbox, I did and had to redo everything.  Virtualbox is really, really easy to use, although VMware server is free and I think VMware player is now free too, and I think they're supposedly more powerful (albeit more difficult to use)

---

### Post by hyper_ch on 2007-08-27
I think vmware has better USB support and vitualbox but I notice virtualbox does use less resources...

for vmware you have to add the commercial repos from canonical... make sure you install vmware SERVER and not the player.

vmware is gratis but you need to register yourself at [www.vmware.com](www.vmware.com) --> just enter email address and get up to 100 serials.

---

