---
title: "Location of PPC mirrors"
date: 2012-01-20
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2012-01-20
I'm installing [PPC Ubuntu](http://cdimage.ubuntu.com/lubuntu/daily/current/), Lubuntu variant.  Installation has stalled at the point when configuring the package manager.  It is asking the hostname of the mirror from which Ubuntu will be downloaded.  None is offered by default.  

Which mirrors offer PPC packages?

---

### Post by rsavage on 2012-01-20
Are you using the alternate install or live/desktop CD to install from?
 
The PowerPC Known Issues page ([https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) ) details a problem that the live CDs have/had with mirrors.  Please confirm the bugs if this is your problem as we need to get it sorted.  
 
The PowerPC FAQ has lots more advice ([https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) ).
 
The powerpc repository is at ports.ubuntu.com with directory /ubuntu-ports/

---

### Post by Lars Noodén on 2012-01-20
> **rsavage said:**
> The powerpc repository is at ports.ubuntu.com with directory /ubuntu-ports/

Thanks.   That did it. 

FWIW, it was the alternate CD.

---

### Post by jharris1993 on 2012-01-31
> **rsavage said:**
> 
 
The powerpc repository is at ports.ubuntu.com with directory /ubuntu-ports/

I am working on an iBook, PPC G3, 700 mhz, 640 megs (max for this box)

I have two instances of Tiger 1.4.11 installed - a previously customized version, and a fresh install (for me to play with!)

I deliberately created extra partitions to install xbuntu 10.4 into - and I "marked" them by formatting them as "unix" from Disk Utility in the Tiger install boot CD.

I did the xbuntu install from the Live CD using my "marked" directories  sincegparted as well as the installer partition utility has fits with the BCD partitioning scheme.  (They show the BCD metadata partitions as "free space" (!!!) )

Everything went well until I tried to run Update Manager. . . .

I too received that looooong laundry list of repositories that did not work.

Using your information - Thanks!  You 'da BOMB! - I opened /etc/apt/sources.list using sudo mousepad.  (IMHO, mousepad beats the living *&$#!! outta nano any day of the week, and twice on Sunday.)

I did a global search and replace for "archives.ubuntu.com/ubuntu" and replaced it with "ports.ubuntu.com/ubuntu-ports"

That fixed a lot of the issues, but I had to go back and do another search-and-replace.  I searched for "http://us." and replaced it with "http://"  since it appears that the "us" repositories could not handle this - I got "bad request" errors.

Having done both of these, I could run an update, ("check" in update manager), without generating errors.

I am now applying the 347 updates that were suggested.

My only beef is that this PPC G3 reminds me of a system running a Pentium II.  It is SOOOOO SLOOOOOW.  ( :OUCH!: )

Again, thanks for all the info, you saved me a LOT of serious head-scratching.  Hopefully I can return the favor sometime.

Jim (JR)

p.s.  I am totally on-board with your reply to that "zen" character (in another thread).  Sheesh! (shaking head in absolute wonder)

---

